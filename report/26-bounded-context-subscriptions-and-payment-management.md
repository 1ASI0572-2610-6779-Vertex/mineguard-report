<h2>4.2. Tactical-Level Domain-Driven Design</h2>

<h3>4.2.1. Bounded Context: Subscriptions and Payment Management</h3>
Se encarga de gestionar las suscripciones de los usuarios y el procesamiento de pagos dentro del sistema. Incluye la administración de planes, ciclos de facturación, renovaciones automáticas, métodos de pago y manejo de transacciones. El objetivo principal de este Bounded Context es garantizar la continuidad del servicio mediante pagos confiables y una correcta gestión del ciclo de vida de las suscripciones.

<h3>4.2.1.1. Domain layer</h3>

Contiene la lógica de negocio y las entidades principales relacionadas a suscripciones y pagos.

**Aggregate: Subscription**
Descripción: Actúa como raíz del agregado y punto central de control del ciclo de vida de la suscripción. Encapsula la lógica de negocio relacionada a activación, cancelación, renovaciones y coordinación de pagos asociados.

|Nombre|Categoría|Descripción|
|-|-|-|
|Subscription|Aggregate Root|Representa la suscripción de un usuario y controla todo su ciclo de vida incluyendo pagos y renovaciones.|

Attributes

|Nombre|Tipo de dato|Visibidad|Descripción|
|-|-|-|-|
|id|Long|Private|Identificador único de la suscripción|
|userId|Long|Private|Identificador del usuario|
|plan|Plan|Private|Plan asociado a la suscripción|
|status|SubscriptionStatus|Private|Estado de la suscripción|
|startDate|Date|Private|Fecha de inicio|
|endDate|Date|Private|Fecha de finalización|
|autoRenew|Boolean|Private|Indica si la suscripción es automática|
|payments|List<Payment>|Private|Pagos asociados a la suscripción|
|paymentMethod|PaymentMethod|Private|Método de pago activo|

Methods

|Nombre|Tipo de retorno|Visibidad|Descripción|
|-|-|-|-|
|activate()|Void|Public|Activa la suscripción|
|cancel()|Void|Public|Cancela la suscripción|
|renew()|Void|Public|Renueva la suscripción|
|processPayment(payment: Payment)|Void|Public|Procesa un pago dentro del agregado|
|retryPayment(paymentId: Long)|Void|Public|Reintenta un pago fallido|
|isActive()|Boolean|Public|Indica si la suscripción está activa|

---

**Entities**

**Payment**
Descripción: Representa un intento o registro de transacción económica dentro de una suscripción. Permite rastrear el estado de cada cobro realizado.

|Nombre|Categoría|Descripción|
|-|-|-|
|Payment|Entity|Representa un pago asociado a una suscripción.|

Attributes

|Nombre|Tipo de dato|Visibidad|Descripción|
|-|-|-|-|
|id|Long|Private|Identificador del pago|
|amount|Money|Private|Monto del pago|
|status|PaymentStatus|Private|Estado del pago|
|createdAt|Date|Private|Fecha del pago|

---

**Plan**
Descripción: Define las condiciones comerciales de una suscripción, incluyendo precio y periodicidad, sirviendo como base para la facturación.

|Nombre|Categoría|Descripción|
|-|-|-|
|Plan|Entity|Define los planes disponibles.|

Attributes

|Nombre|Tipo de dato|Visibidad|Descripción|
|-|-|-|-|
|id|Long|Private|Identificador del plan|
|name|String|Private|Nombre del plan|
|price|Money|Private|Precio del plan|
|billingCycle|String|Private|Ciclo de facturación|

---

**PaymentMethod**
Descripción: Representa la forma en la que el usuario realiza los pagos, permitiendo reutilización y validación en múltiples transacciones.

|Nombre|Categoría|Descripción|
|-|-|-|
|PaymentMethod|Entity|Método de pago del usuario.|

Attributes

|Nombre|Tipo de dato|Visibidad|Descripción|
|-|-|-|-|
|id|Long|Private|Identificador|
|type|String|Private|Tipo de método|
|details|String|Private|Detalles del método|

---

**Value Objects**

|Nombre|Descripción|
|-|-|
|Money|Representa valores monetarios|
|SubscriptionStatus|Estado de la suscripción|
|PaymentStatus|Estado del pago|

---

**Commands**

CreateSubscriptionCommand <>  
CancelSubscriptionCommand <>  
RenewSubscriptionCommand <>  
ProcessPaymentCommand <>  
RetryPaymentCommand <>  
UpdatePaymentMethodCommand <>  

---

**Queries**

GetSubscriptionByIdQuery <>  
GetSubscriptionsByUserQuery <>  
GetPlansQuery <>  

---

**Services**

SubscriptionCommandService

handle(CreateSubscriptionCommand)  
handle(CancelSubscriptionCommand)  
handle(RenewSubscriptionCommand)  
handle(ProcessPaymentCommand)  
handle(RetryPaymentCommand)  
handle(UpdatePaymentMethodCommand)  

SubscriptionQueryService

handle(GetSubscriptionByIdQuery)  
handle(GetSubscriptionsByUserQuery)  
handle(GetPlansQuery)  

---

<h3>4.2.1.2. Interface Layer</h3>

**Rest Controllers**

SubscriptionsController
Descripción: Expone endpoints REST para gestionar el ciclo de vida de las suscripciones, incluyendo creación, cancelación y renovación.

|Método|Ruta|Descripción|
|-|-|-|
|getSubscriptionById()|GET /api/v1/subscriptions/{id}|Obtiene una suscripción|
|getSubscriptionsByUser()|GET /api/v1/subscriptions/user/{userId}|Lista suscripciones|
|createSubscription()|POST /api/v1/subscriptions|Crea suscripción|
|cancelSubscription()|POST /api/v1/subscriptions/{id}/cancel|Cancela suscripción|
|renewSubscription()|POST /api/v1/subscriptions/{id}/renew|Renueva suscripción|

PaymentsController
Descripción: Maneja las operaciones relacionadas al procesamiento y reintento de pagos dentro de una suscripción.

|Método|Ruta|Descripción|
|-|-|-|
|processPayment()|POST /api/v1/subscriptions/{id}/payments|Procesa pago|
|retryPayment()|POST /api/v1/subscriptions/{id}/payments/{paymentId}/retry|Reintenta pago|

PlansController
Descripción: Permite consultar los planes disponibles que pueden ser contratados por los usuarios.

|Método|Ruta|Descripción|
|-|-|-|
|getPlans()|GET /api/v1/plans|Obtiene planes|

---

**Resources**

CreateSubscriptionResource <>  
SubscriptionResource <>  
PaymentResource <>  
PlanResource <>  

---

**Assemblers**

CreateSubscriptionCommandFromResourceAssembler  
SubscriptionResourceFromEntityAssembler  
PaymentResourceFromEntityAssembler  
PlanResourceFromEntityAssembler  

---

<h3>4.2.1.3. Application Layer</h3>

SubscriptionCommandService
Descripción: Implementa la lógica de aplicación para ejecutar operaciones que modifican el estado de las suscripciones.

|Método|Descripción|
|-|-|
|handle(CreateSubscriptionCommand)|Crea suscripción|
|handle(CancelSubscriptionCommand)|Cancela suscripción|
|handle(RenewSubscriptionCommand)|Renueva suscripción|
|handle(ProcessPaymentCommand)|Procesa pago|
|handle(RetryPaymentCommand)|Reintenta pago|
|handle(UpdatePaymentMethodCommand)|Actualiza método de pago|

SubscriptionQueryService
Descripción: Implementa la lógica para recuperar datos de suscripciones sin alterar el estado del sistema.

|Método|Descripción|
|-|-|
|handle(GetSubscriptionByIdQuery)|Obtiene suscripción|
|handle(GetSubscriptionsByUserQuery)|Lista suscripciones|
|handle(GetPlansQuery)|Lista planes|

---

<h3>4.2.1.4. Infrastructure Layer</h3>

SubscriptionRepository
Descripción: Gestiona la persistencia de las suscripciones y permite consultas específicas sobre ellas.

|Método|Tipo de Retorno|Descripción|
|-|-|-|
|findByUserId|List|Obtiene suscripciones por usuario|
|findByStatus|List|Filtra por estado|
|findById|Optional|Busca por ID|

PlanRepository
Descripción: Provee acceso a los datos de planes disponibles en el sistema.

|Método|Tipo de Retorno|Descripción|
|-|-|-|
|findAll|List|Obtiene todos los planes|
