# вторая работа по mongodb

## удаление коллекции

test> db.users.drop()

true

## показ оставшихся коллекций

test> show collections

messages

## показ не изменённой коллекции

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

## показ изменений

test> db.messages.findOneAndReplace({}, {'name': 'danya'})

{
  _id: ObjectId('65fab460a9627c1356232498'),
  message: 'как дела',
  name: 'danya'
}

## удаление документа из коллекции

test> db.messages.findOneAndDelete({}, {'name': 'danya'})

{ _id: ObjectId('65fab460a9627c1356232498'), name: 'danya' }

