# lookup, но почему-то не вывел значения из поля as:


test> db.users.aggregate([{ $lookup: { from: 'messages', localField: 'name', foreignField: 'name', as: 'message'}}])


[
  {
    _id: ObjectId('65f9a9b877bdc2568b5d1ab9'),
    name: 'Danya',
    message: []
  },
  { _id: ObjectId('65fab4d3a9627c1356232499'), age: '23', message: [] }
]


# обновление, но кажется я добавил объект командой update

test> db.messages.findOneAndUpdate({}, { $set: {'name': 'danya', 'message': 'как дела'}})
{
  _id: ObjectId('65fab460a9627c1356232498'),
  message: 'как дела',
  name: 'danya'
}
test> 

   2024-03-20T14:06:13.754+03:00: /sys/kernel/mm/transparent_hugepage/enabled is 'always'. We suggest setting it to 'never'
   2024-03-20T14:06:13.755+03:00: vm.max_map_count is too low
------


# структура базы

test> db.users.find()

[
  { _id: ObjectId('65f9a9b877bdc2568b5d1ab9'), name: 'Danya' },
  { _id: ObjectId('65fab4d3a9627c1356232499'), age: '23' }
]
test> db.messages.find({})

[
  {
    _id: ObjectId('65fab460a9627c1356232498'),
    message: 'как дела',
    name: 'danya'
  },
  {
    _id: ObjectId('65fac73acccd488603f2aa44'),
    name: 'danya',
    message: 'привет'
  }
]
test> 


