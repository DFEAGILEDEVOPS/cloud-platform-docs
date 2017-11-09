============
The Platform
============

This chapter provides a high-level overview of the platform design from a user expective. The primary users of the platform are intended to be teams building or maintaining digital services with a self-service devops user experience. During the pilot, the ground truth of the design is the configuration that builds the OCP plant and templates which deploy sample code from VSTS. 

At this point of the project, this design chapter is quite heavy on principles. This allows people who are trying understand the platform to understand the self-service operating model the platform is aiming to enable to enable. Being explicit about the design principles allows people to challenge the model and whether the approach and fits within the wider organization. It also allows pilot users of the platform to point out where the current prototypes or design deviates from the principles. 


Design Principles
-----------------

The primary design principles of the platform are: 

* Automation, standardization and isolation
* Control only the things that matter
* Treat infrastructure as code
* State as managed services
* Scale down as well as up

These principles and examples of how they affect the platform are outlined in the following sections. 

Automation, Standardisation and Isolation 
-----------------------------------------

    As technology advances, it reverses the characteristics of every situation again and again. The age of automation is going to be the age of 'do it yourself.'

    -- Marshall McLuhan

Computers are very good at repetitive tasks. By maximising automation we free people to do high-value tasks. This leads to the outcome of a happy and sustainable culture of delivery. Automation should, therefore, be maximised. Where decisions should be made by humans, the decision should be to press a literal (or metaphorical) "Big Green Button" when they are ready to make the decision. The outcome of the decision should be automated and immediate. 

    Today’s standardization… is the necessary foundation on which tomorrow’s improvements will be based.  If you think “standardization” as the best you know today, but which is to be improved tomorrow – you get somewhere.  But if you think of standards as confining, then progress stops. 
    
    -- Henry Ford

Standardisation compliments automation by making it possible for new teams to use automation that was built in a specific context and with implicit assumptions. Without standardization, automation cannot be easily shared. An environment that has lots of automation that is specific to many small and repetitive contexts grows in complexity over time. Automation compliments standardization as manual actions may deviate from the intended standard through human error or stale knowledge of the latest standards. 

    Use appropriate isolation.

    -- Paul Cripwell
    
Isolation compliments automation in that the consequence of erroneous automation can be minimised (e.g. you clicked the wrong button). Isolation removes the risk allowing an empowered team member to make the decisions to proceed. Often people external to the team are left "in the loop" to compensate for high risks of human error. A remote risk of a very bad outcome is used to justify the substantial costs of waiting for a meeting to bless a decision. The effect of human circuit breakers has a disproportionate when the decision is to be made by a consultatory committee rather than an empowered team member. Good isolation helps mitigate long tail risks allowing teams to avoid the disproportionate costs of decision meeting delays. Decisions should be made at the most appropriate level and good isolation moves the appropriate level into the delivery team. 


