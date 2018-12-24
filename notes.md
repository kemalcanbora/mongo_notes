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

# Set and unset 
Her  dokumana a field eklemek için set
db.user_information.update({},
                          {$set : {"proper_job":""}},
                          {upsert:false,
                          multi:true}) 
                          
                          
Her dokumandan istenen fieldı siler
db.user_information.update({},
                          {$unset : {"proper_job":1}},
                          {upsert:false,
                          multi:true}) 

# Find duplucate

db.users.aggregate([
  { $group: { 
    _id: { firstField: "$UserLinkedinUrl", secondField: "$UserLinkedinUrl" }, 
    uniqueIds: { $addToSet: "$_id" },
    count: { $sum: 1 } 
  }}, 
  { $match: { 
    count: { $gt: 1 } 
  }}
])
 
