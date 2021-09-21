# Java/Kotlin & Vaadin in Spring
- Completable Future cannot access the vaadin session scope
```kotlin
CompletableFuture.supplyAsync {
  val user = getCurrentUser()
  user // user is null if we use: SpringVaadinSession.getCurrent() and custom http session context
}
```
**Resolution**: we need to pass the parameter from function scope to inside the threads of completable future.
