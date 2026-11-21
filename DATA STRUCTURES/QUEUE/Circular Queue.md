

## Queue Basics

### Definition

Queue follows FIFO (First In First Out).

```
Front → [10][20][30] ← Rear
```

10 enters first → leaves first.

### Queue Operations

|Operation|Meaning|
|---|---|
|`enqueue(x)`|Add element at rear|
|`dequeue()`|Remove element from front|
|`Front()`|Get first element|
|`Rear()`|Get last element|
|`isEmpty()`|Check queue empty|
|`isFull()`|Check queue full|

## Why Circular Queue?

Normal queue problem:

```
[10][20][30][ ][ ]
```

After dequeue:

```
[ ][20][30][ ][ ]
```

Space wasted ❌

Circular queue reuses space:

```
[ ][20][30][40][50] ↑              ↓ ← ← ← ← ← ← ←
```

## Variables Needed

java

```
int[] queueint frontint rearint size
```

Initial state:

```
front = -1rear = -1
```

Meaning: Queue empty.

## Important Conditions

### Queue Empty

java

```
front == -1
```

### Queue Full ⭐

Queue is full when:

java

```
(rear + 1) % size == front
```

Meaning: Next position of rear hits front.

> [!tip] Memory Trick Rear next position == Front → FULL

## Enqueue Operation

### Case 1: Queue empty

java

```
front = 0rear = 0
```

Insert element.

### Case 2: Normal insertion

Move rear:

java

```
rear = (rear + 1) % sizequeue[rear] = value
```

## Dequeue Operation

> [!important] Rule Dequeue always moves front.

### Case 1: Only one element

Condition:

java

```
front == rear
```

After removal:

java

```
front = -1rear = -1
```

Queue empty.

### Case 2: Multiple elements

Move front:

java

```
front = (front + 1) % size
```

## Important Rule ⭐

> [!note] Remember
> 
> - `enqueue` → rear moves
> - `dequeue` → front moves

## Front Function

Correct:

java

```
return queue[front]
```

Wrong:

java

```
return queue[rear] ❌
```

## Rear Function

java

```
return queue[rear]
```

## Full Code

java


class MyCircularQueue {

    int[] queue;
    int front;
    int rear;
    int size;

    public MyCircularQueue(int k) {
        queue = new int[k];
        size = k;
        front = -1;
        rear = -1;
    }

    public boolean enQueue(int value) {
        if(isFull())
            return false;

        if(front == -1){
            front = 0;
            rear = 0;
        }
        else{
            rear = (rear + 1) % size;
        }

        queue[rear] = value;
        return true;
    }

    public boolean deQueue() {
        if(isEmpty())
            return false;

        if(front == rear){
            front = -1;
            rear = -1;
        }
        else{
            front = (front + 1) % size;
        }

        return true;
    }

    public int Front() {
        if(isEmpty())
            return -1;

        return queue[front];
    }

    public int Rear() {
        if(isEmpty())
            return -1;

        return queue[rear];
    }

    public boolean isEmpty() {
        return front == -1;
    }

    public boolean isFull() {
        return (rear + 1) % size == front;
    }
}



## Visual Memory Tricks ⭐

|State|Condition|
|---|---|
|Empty Queue|`front = -1`, `rear = -1`|
|One Element|`front == rear`|
|Multiple Elements|`front != rear`|

## Most Important Formulas ⭐

java


rear = (rear + 1) % size
front = (front + 1) % size
(rear + 1) % size == front


> [!success] If you remember these → circular queue easy.

## Common Beginner Mistakes ⚠️

### Mistake 1: Returning rear in Front()

❌ Wrong:

java

```
return queue[rear]
```

✅ Correct:

java

```
return queue[front]
```

### Mistake 2: Forgetting single element case

Must check:

java

```
if(front == rear)
```

### Mistake 3: Forgetting modulo

❌ Wrong:

java

```
rear++
```

✅ Correct:

java

```
rear = (rear + 1) % size
```

### Mistake 4: Thinking we delete element

We don't delete. We just move pointer.

### Mistake 5: Forgetting empty condition

Always check:

java

```
if(isEmpty())
```

## Interview Memory Summary ⭐

> [!abstract] Just Remember This
> 
> - Empty → `front = -1`
> - Insert first element → `front = 0`, `rear = 0`
> - enqueue → rear moves
> - dequeue → front moves
> - Full → rear next == front

## Ultra Short Revision

> [!quote] 1 Minute Revision
> 
> - Queue → FIFO
> - Empty: `front = -1`
> - Full: `(rear+1) % size == front`
> - enqueue: rear moves
> - dequeue: front moves
> - `Front()`: `queue[front]`
> - `Rear()`: `queue[rear]`