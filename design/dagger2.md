# Dagger 2

Relies on generated code instead of reflection which means it can't access private properties. Code is generated by annotations.

## Annotations

1. **@Module** & **@Provide**: classes & methods providing dependencies
2. **@Inject**: request dependencies

## @Module & @Provide

@module annotates the class that provides dependencies
@provide annotates methods in the (@module) class which actually provide dependencies

## @Component

annotates an interface that connects providers and consumers (performs DI using providers). Interface used by d2 to generate class, "Dagger{ComponenName}".

- DI isn't automatic and you need to go through the generated component class
- to use field injection for a given class ``NeedDependency``, define a method in component interface which *accepts* an isntance of the class which needs dependencies injected (``NeedDependency`` in this case)

```kotlin
@Component
interface ExampleComponent {
    fun inject(instance : NeedDependency)
}
```