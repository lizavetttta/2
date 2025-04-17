package javaapplication5;
public class JavaApplication5 {
    public static void main(String[] args) {
        Queue queue = new Queue(5);
        queue.enqueue(1);
        queue.enqueue(2);
        queue.enqueue(3);
        System.out.println("Первый элемент: " + queue.peek());
        System.out.println("Удаляем элемент: " + queue.dequeue()); 
        System.out.println("Текущий размер очереди: " + queue.size()); 
    }

    public static class Queue {
        private int[] elements; 
        private int front;      
        private int rear;       
        private int size;       
        private int capacity;   

        // Конструктор
        public Queue(int capacity) {
            this.capacity = capacity;
            elements = new int[capacity];
            front = 0;
            rear = -1;
            size = 0;
        }

        // Метод для добавления элемента в очередь
        public void enqueue(int item) {
            if (size == capacity) {
                throw new IllegalStateException("Очередь переполнена");
            }
            rear = (rear + 1) % capacity; 
            elements[rear] = item;
            size++;
        }

        // Метод для удаления элемента из очереди
        public int dequeue() {
            if (isEmpty()) {
                throw new IllegalStateException("Очередь пуста");
            }
            int item = elements[front];
            front = (front + 1) % capacity;
            size--;
            return item;
        }

        // Метод для проверки, пуста ли очередь
        public boolean isEmpty() {
            return size == 0;
        }

        // Метод для получения текущего размера очереди
        public int size() {
            return size;
        }

        public int peek() {
            if (isEmpty()) {
                throw new IllegalStateException("Очередь пуста");
            }
            return elements[front];
        }
    }
}
