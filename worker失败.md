客户端提交任务给master，由master分配任务给可用的workers。这些worker接收被分配的任务，一旦这些任务被执行它们就会上报状态。master随后就会通知客户端执行的结果。

如果一个worker奔溃，所有分配给它的未完成的任务必须被重新分配。第一个要求就是给master能够检测worker奔溃的能力。master必须能够检测到何时一个worker奔溃了，同时也能确定哪些worker能够执行它的任务。当一个worker奔溃时，它可能最终部分的执行了任务，或者完全执行完了任务但是还未来得及上报结果。如果计算还有副作用的话，为了清理状态某些恢复步骤可能就很有必要了。

