---
title: "在受管理的類別類型宣告 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __gc types
- classes [C++], managed
- class keyword [C++], CLR
- __value keyword
- value types, declaring
- value keyword [C++]
- managed classes
- interface class keyword
- ref keyword [C++]
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 182cb637351f722677d8da97c7a7b880c3241311
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="declaration-of-a-managed-class-type"></a>Managed 類別類型的宣告
若要宣告參考類別的型別，從 Managed Extensions for c + + 變更為 Visual c + + 方法。  
  
 在 Managed Extensions，參考類別類型前面加上`__gc`關鍵字。 在新語法中，`__gc`關鍵字取代為兩個含空格的關鍵字：`ref class`或`ref struct`。 選擇`struct`或`class`表示公用 (如`struct`) 或私用 (如`class`) 在初始未標記類型的主體區段中宣告其成員的預設存取層級。  
  
 同樣地，在 Managed Extensions，實值類別類型前面加上`__value`關鍵字。 在新語法中，`__value`關鍵字取代為兩個含空格的關鍵字：`value class`或`value struct`。  
  
 介面型別，在 Managed Extensions，指出與關鍵字`__interface`。 在新語法中，這會取代`interface class`。  
  
 例如，下列類別宣告在 Managed Extensions:  
  
```  
public __gc class Block {};     // reference class  
public __value class Vector {}; // value class  
public __interface IFooBar {};  // interface class  
```  
  
 在新語法中這些對等程式碼宣告，如下所示：  
  
```  
public ref class Block {};         // reference class  
public value class Vector {};      // value class  
public interface class IFooBar {}; // interface class  
```  
  
## <a name="specifying-the-class-as-abstract"></a>指定的類別為抽象  
 在受管理的擴充功能，您將關鍵字放`__abstract`之前`class`關鍵字 (在之前或之後`__gc`) 來指示此類別是不完整，而且在程式內，無法建立類別的物件：  
  
```  
public __gc __abstract class Shape {};  
public __gc __abstract class Shape2D: public Shape {};  
```  
  
 在新語法中，您指定`abstract`遵循類別名稱和類別主體、 基底類別衍生清單或分號前的內容關鍵字。  
  
```  
public ref class Shape abstract {};  
public ref class Shape2D abstract : public Shape{};  
```  
  
 當然，語意不變。  
  
## <a name="specifying-the-class-as-sealed"></a>指定為密封的類別  
 在受管理的擴充功能，您將關鍵字放`__sealed`之前`class`關鍵字 (之前或之後`__gc`) 來表示類別的物件，無法繼承自：  
  
```  
public __gc __sealed class String {};  
```  
  
 在新語法中，您指定`sealed`遵循類別名稱和類別主體、 基底類別衍生清單或分號前的內容關鍵字。  
  
 您可以同時衍生類別，並請將它密封。 例如，`String`類別隱含衍生自`Object`。 密封類別的優點是它支援靜態解析 (也就是在編譯時期) 透過密封的參考類別物件的所有虛擬函式呼叫。 這是因為`sealed`規範可確保`String`追蹤控制代碼可能會提供覆寫執行個體所叫用虛擬方法的後續的衍生類別不能參考。 以下是範例密封類別的新語法中：  
  
```  
public ref class String sealed {};  
```  
  
 其中也可以指定類別為這兩個抽象和密封-這是表示靜態類別的特殊情況。 這是 CLR 文件所述，如下所示：  
  
 "的類型，它是同時`abstract`和`sealed`應該擁有只有靜態成員，並可做為什麼某些語言呼叫命名空間。 」  
  
 例如，這裡是使用 Managed Extensions 語法抽象密封類別的宣告：  
  
```  
public __gc __sealed __abstract class State {  
public:  
   static State() {}  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
 此外，這裡有這項宣告轉譯成新的語法：  
  
```  
public ref class State abstract sealed {  
public:  
   static State();  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
## <a name="clr-inheritance-specifying-the-base-class"></a>CLR 繼承： 指定的基底類別  
 CLR 物件模型中，支援公用的單一繼承。 不過，受管理的擴充功能會保留 ISO c + + 預設解譯，而不存取關鍵字與指定的私人衍生的基底類別。 這表示每個 CLR 繼承宣告必須提供`public`關鍵字來覆寫的預設解譯。  
  
```  
// Managed Extensions: error: defaults to private derivation  
__gc class Derived : Base {};  
```  
  
 在新語法定義中，沒有存取關鍵字會指出 CLR 繼承定義中的公用衍生。 因此，`public`存取關鍵字現在是選擇性。 雖然這不需要任何修改的 Managed Extensions for c + + 程式碼，我會列出此變更此處的完整性。  
  
```  
// New syntax: ok: defaults to public derivation  
ref class Derived : Base{};  
```  
  
## <a name="see-also"></a>另請參閱  
 [Managed 類型 (C + + CL)](../dotnet/managed-types-cpp-cl.md)   
 [類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)   
 [abstract](../windows/abstract-cpp-component-extensions.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)