![Exported image](Exported%20image%2020260212171551-0.png) ![Exported image](Exported%20image%2020260212171553-1.png) ![Exported image](Exported%20image%2020260212171556-2.png) ![Exported image](Exported%20image%2020260212171558-3.png) ![Exported image](Exported%20image%2020260212171606-4.png) ![Exported image](Exported%20image%2020260212171607-5.png) ![Exported image](Exported%20image%2020260212171609-6.png) ![Exported image](Exported%20image%2020260212171611-7.png) ![Exported image](Exported%20image%2020260212171613-8.png) ![Exported image](Exported%20image%2020260212171615-9.png) ![Exported image](Exported%20image%2020260212171620-10.png) ![Exported image](Exported%20image%2020260212171626-11.png) ![Exported image](Exported%20image%2020260212171632-12.png) ![Exported image](Exported%20image%2020260212171633-13.png) ![Exported image](Exported%20image%2020260212171639-14.png) ![Exported image](Exported%20image%2020260212171642-15.png) ![Exported image](Exported%20image%2020260212171644-16.png) ![Exported image](Exported%20image%2020260212171646-17.png) ![Exported image](Exported%20image%2020260212171651-18.png)

![[clumbia 论文导读.pdf]]

为什么rule binding 不会出现漏绑定的情况呢  
我觉得是因为 rule binding 是在 apply rule 发生的，apply rule 这个任务是在  
Opt_exp 的时候被压入的，opt_exp 压入这个任务之后会直接压入E_GROUP，栈反向执行，在执行apply rule的时候子节点都已经做过充分逻辑优化了，这个时候 再binding 子节点，可以保证不重复绑定了【真的可以吗？】

注意这里，出发 O_EXPX 任务，要优化的话是生成的这个新的 M_EXP，不是子节点，上面 O_EXP 在压栈 APPLY_RULE 之后 EXPEND 的是子GROUP

注意这边，压栈 apply rule 之前只对 top op 做了检查，这个时候 sub patttern 可能是不满足的，但是没关系，我先把当前 mexp 的 apply rule 压进去，然后先 expend 子 group， 让他们尽可能应用更多的逻辑计划，为什么一定是逻辑呢，因为只有逻辑算子可以 apply rule，所以就不费劲生成物理算子了，如果子节点应用物理计划，那么生成的是物理节点，记住生成子节点是为了给当前节点应用规则用的，如果子节点是物理算子，那么就无法应用了。