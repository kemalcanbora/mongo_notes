# Update

- db.dress.updateMany(
   {brand_name: "H&M TR" },
   { $set: { brand_name: "HM" } },
   { upsert: true }
)

# Multiple filter 
<br> db.dress.find({ $and : [
   <br>     {category : { $exists: true}, category : "Ayakkabı" },
   <br>   {color  : { $exists: true}, color : {$in:["Kırmızı","Mavi"] }},
   <br>    {brand_name  : { $exists: true} },
   <br>     {last_price: { $exists: true}, last_price : {$gte: 0, $lte: 1550.5} }
   <br> ]})

# show field items
<br> db.dress.distinct("category")
