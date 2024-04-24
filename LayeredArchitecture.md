# Layered Architecture

## Main Points:

1. **Introduction to Architectural Patterns**:
   - Discusses the importance of architectural patterns in balancing requirements and architectural concerns.
   - Differentiates between design patterns and architectural patterns, highlighting the complexity and composability of the latter.

2. **Big Ball of Mud Architecture**:
   - Describes the absence of structure in this architecture, with ad hoc connections between components.
   - Illustrates the challenges of making changes in such architectures due to extensive ripple effects.

3. **Layered Architecture**:
   - Introduces layered architecture as a more organized alternative to the big ball of mud.
   - Explains the concept of closed layers and how they contribute to separation of concerns and isolation.
     - Closed layers ensure requests must traverse through all layers, promoting separation and clean architecture.
     - Layers communicate through well-defined interfaces, reducing coupling and facilitating changes.
   - Discusses the benefits of layered architecture, including easier maintenance and the ability to swap components without extensive ripple effects.
   - Considers the trade-offs of opening layers for optional functionalities and its impact on coupling and isolation.

4. **Layers of Isolation and Trade-offs**:
   - Layers of isolation ensure clean separation and defined communication paths.
   - Advantages:
     - Clear separation of concerns: Each layer handles specific functionalities, enhancing maintainability.
     - Reduced coupling: Interfaces facilitate communication, minimizing dependencies between layers.
     - Ease of change: Changes within a layer have limited impact, reducing ripple effects across the system.
   - Trade-offs:
     - Opening layers for optional functionalities increases flexibility but may compromise isolation and introduce coupling.
     - Architectural sinkhole anti-pattern may arise when layers are bypassed, undermining the integrity of the architecture.
     - Balancing openness and isolation requires careful consideration of trade-offs and governance.

5. **Pattern Governance**:
   - Pattern governance ensures adherence to architectural principles and objectives.
   - Challenges arise when deviating from established patterns, risking architectural integrity.
   - Architects must balance flexibility with consistency, addressing unusual problems within the architectural pattern.
   - Maintaining pattern fidelity prevents gradual erosion of architectural benefits and promotes long-term sustainability.

## Next Steps:
   - Mentions transitioning to discussing microkernel architecture as the next topic.

# Event-Driven Architecture: Understanding Broker and Mediator Topologies

## Introduction to Distributed Architectures

In the realm of distributed architectures, systems may operate across multiple process spaces. A key approach within this domain is event-driven architecture, which leverages events as the primary means of communication between components. This transcript delves into two flavors of event-driven architecture: the broker topology and the mediator topology.

## Broker Topology

In a broker topology event-driven architecture, the following components are central:

- **Event Channel**: Represents the conduit for events, often implemented using message queues.
- **Initiating Event**: Serves as the trigger for a process.
- **Event Processors**: Entities responsible for performing tasks within the architecture.

### Workflow Example: Insurance Company Business Process

Consider an insurance company's business process triggered by a customer's relocation:

1. The customer's relocation event prompts the Customer Processor to update the customer's address in the system of records.
2. Upon address update, a message is posted to a message queue, which is monitored by both the Quote and Claims processors.
3. Concurrently, the Quote Processor recalculates any outstanding quotes, while the Claims Processor updates related claims.
4. Subsequently, adjustments are made if necessary, and a notification email is generated for the customer.

### Challenges and Considerations

- **Error Handling**: Error management is crucial, as system failures during processing can disrupt workflows. Strategies such as error queues or verification mechanisms are necessary.
- **Workflow Evolution**: Modifying workflows, such as incorporating new processes like auditing, requires thoughtful integration into the existing architecture.
- **Coordination**: Asynchronous nature necessitates careful coordination, especially for unified notifications, which often occur at the end of processes.

## Mediator Topology

In contrast, a mediator topology introduces an additional architectural component: the event mediator. This mediator orchestrates interactions between components and ensures that

Why do we have them, when and where would we use them, advantages and disadvantages of both
