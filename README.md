# queue
Amazon Builder Library のキューバックログの回避の記事を読んで、pythonでQueの実装記事を参考にQue処理を試してみました。

乗り越えられないキューバックログの回避　https://aws.amazon.com/jp/builders-library/avoiding-insurmountable-queue-backlogs/?did=ba_card&trk=ba_card  
Pythonでキューイング処理　https://qiita.com/okuhiiro/items/7e4813d8f44a40e23938  

class Queue(object):
    def __init__(self):
        self.queue_list = []

    # enqueue 待ち行列に入れる、キューに入れる
    def enqueue(self, value):
        self.queue_list.append(value)

    # dequeue 待ち行列からはずす
    def dequeue(self):
        try:
            # 先頭をとりだす
            value = self.queue_list.pop(0)
        except IndexError:
            value = None

        return value
        
queue = Queue()

queue.enqueue("a")
queue.enqueue("b")
queue.enqueue("c")

print(queue.dequeue()) # aを出力
print(queue.dequeue()) # bを出力
print(queue.dequeue()) # cを出力
print(queue.dequeue()) # None
