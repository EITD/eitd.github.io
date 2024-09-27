---
layout: post
section-type: post
has-comments: true
title: "Serializable"
category: java
---

> `Serializable` is to convert the runtime object state to binary, and then save it to stream, memory or network to transfer it to other ends.
> 

## Differences between Serializable and Parcelable

1. `Parcelable` is faster than `Serializable` interface.
2. `Parcelable` interface takes more time to implement.
3. `Serializable` interface is easier to implement.
4. `Serializable` creates a lot of temporary objects and causes garbage collection.
5. `Parcelable` array can be passed via `Intent`.

```java
import java.io.Serializable;

class serializableObject implements Serializable {
   String name;
   public serializableObject(String name) {
      this.name = name;
   }
   public String getName() {
      return name;
   }
}
```

```java
import android.os.Parcel;
import android.os.Parcelable;

class parcleObject implements Parcelable {
   private String name;
   protected parcleObject(Parcel in) {
      this.name = in.readString();
   }
   public parcleObject(String name) {
      this.name = name;
   }
   public String getName() {
      return name;
   }
   public void setName(String name) {
      this.name = name;
   }
   public static final Creator<parcleObject> CREATOR = new Creator<parcleObject>() {
      @Override
      public parcleObject createFromParcel(Parcel in) {
         return new parcleObject(in);
      }
      @Override
      public parcleObject[] newArray(int size) {
         return new parcleObject[size];
      }
   };
   @Override
   public int describeContents() {
      return 0;
   }
   @Override
   public void writeToParcel(Parcel dest, int flags) {
      dest.writeString(this.name);
   }
}
```

- `createFromParcel(Parcel in)`
    
    Create original object from parcelable object.
    
- `newArray(int size)`
    
    Create an array of original object with specific length.
    
- `describeContents()`
    
    Return description contents.
    
- `writeToParcel(Parcel dest, int flags)`
    
    Write current object to parcel structure.