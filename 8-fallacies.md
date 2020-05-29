## [NOTES] The 8 fallacies of distributed computing 

## Acknowledgements
- [Fallacies of Distributed Computing Explained](https://pages.cs.wisc.edu/~zuyu/files/fallacies.pdf)

## Notes

#### 8 fallacies (rules that should be always followed)
1. Make a reliable network
2. A network that has zero latency
3. Strive for infinite bandwidth 
4. Create a secure network 
5. Keep the topology consistent 
6. Only have 1 admin (single source of truth)
7. Utilize cost-effective solutions that make it almost "free" (resource & time wise)
8. Create a homogeneous network (all servers have same config) 

#### 1 | Make a reliable network
- Use reliable messaging services like MSMQ 
<ul>
  <li>If not available remember to:</li>
  <ul>
    <li>acknowledge import messages</li>
    <li>identify + ignore the duplicates</li>
    <li>verify message integrity</li>
    <li>order messages accordingly</li>
  </ul>
</ul>

#### 2 | A network that has zero latency
- Latency becomes an issue when you move to WAN (but not LAN) 
- Distributed objects can be expensive to call
<ul>
  <li>When making calls</li>
  <ul>
    <li>Minimize # of calls</li>
    <li>Move as much data in each of the calls</li>   
  </ul>
</ul>
- AJAX is a good way to call data in the background 
- IF AJAX is too SLOW -> it could make the app unresponsive
<ul>
  <li>Good tools for measuring latency</li>
  <ul>
    <li>Opnet Modeler</li>
  </ul>
</ul>
