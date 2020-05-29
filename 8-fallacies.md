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

#### 3 | Strive for infinite bandwidth
- Need to remember to minimize the size of info before send
- Need to think of production situation where bandiwdth isn't infinite
- Remember to consider how much data is being sent over each call
- When developing -> stimulate production environment as much as possible

#### 4 | Create a secure network
- Need to perform threat modeling to evaluate security risks + severity
- Understand the tradeoff between costs/risks/probability of happening

<ul>
  <li>Security affects the following levels</li>
  <ul>
    <li>Network</li>
    <li>Infrastructure</li>
    <li>Application (production level)</li>
  </ul>
</ul>

#### 5 | Keep the topology consistent
- Do NOT depend on specific endpoitns/routes as those can always change
- Provide location transparency (ex. using ESB)
- Provide discovery services (ex. active directory)
- DNS names > IP addresses 

<ul>
  <li>If topology is consistent</li>
  <ul>
    <li>can reduce resource expenses (don't have to change things everytime the topology changes) </li>
    <li>messages can know the path it needs to travel in advance</li>
  </ul>
</ul>

#### 6 | Only have 1 admin
- Very important especially when you start collaborating with 3rd parties and need to manage permissions 
- Setting the roles clearly is important -> for testing/debugging/diagnosing problems

#### 7 | Utilize cost-effective solutions that make it almost "free" 
- Everytime data is called in production level it costs a lot (both time and resources) for the host and user, we want to strive to minimize the cost as much as possible (think if we're serving for like 1 billion users)
- Resource costs: servers/routers/security/maintaince etc
-TL;DR -> make your network effective and efficient
