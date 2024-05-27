# Intent && Bundle

## What is Intent?

1. Launch `Activity`
2. Start `Service`
3. Message `Broadcast`
4. Display Web Page
5. Display Contact List

![Untitled](Intent%20&&%20Bundle%20f85ab0cbb96c47128de36510a77ee1a3/Untitled.png)

## Implicit && Explicit

- **Implicit**
    
    > Component can’t be specifying. The system will filter out component which will response to the action.
    > 
    
    ```kotlin
    Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));
    startActivity(intent);
    ```
    
- **Explicit**
    
    > Component can be specified. The specified target component will be invoked.
    > 
    
    ```kotlin
    Intent i = new Intent(getApplicationContext(), ActivityTwo.class);
    startActivity(i);
    ```
    

## Bundle

> Bundles are used to **pass** the required **data** between various Android activities.
> 

```java
Bundle b = new Bundle();
b.putString("Email","abc@xyz.com");
i.putExtras(b); // where i is intent
```