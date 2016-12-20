---
title: "Managed 類別類型的宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__gc 類型"
  - "__value 關鍵字"
  - "class 關鍵字 [C++], CLR"
  - "類別 [C++], Managed"
  - "interface class 關鍵字"
  - "Managed 類別"
  - "ref 關鍵字 [C++]"
  - "value 關鍵字 [C++]"
  - "實值類型, 宣告"
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Managed 類別類型的宣告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，宣告參考類別型別的方式已變更。  
  
 在 Managed Extensions 中，參考類別型別是以 `__gc` 關鍵字做為開端。  在新語法中，下列兩個間隔關鍵字中的其中一個會取代 `__gc` 關鍵字：`ref class` 或 `ref struct`。  選擇 `struct` 或 `class` 是針對在型別主體的初始未標記區段中所宣告的成員，指出其為公用 \(針對 `struct`\) 或私用 \(針對 `class`\) 預設存取層級。  
  
 同樣地，在 Managed Extensions 中，實值類別型別是以 `__value` 關鍵字做為開端。  在新語法中，下列兩個間隔關鍵字中的其中一個會取代 `__value` 關鍵字：`value class` 或 `value struct`。  
  
 在 Managed Extensions 中，是以關鍵字 `__interface` 表示介面型別。  在新語法中，則以 `interface class` 取代。  
  
 例如，以下為 Managed Extensions 中的類別宣告：  
  
```  
public __gc class Block {};     // reference class  
public __value class Vector {}; // value class  
public __interface IFooBar {};  // interface class  
```  
  
 而在新語法下的同等宣告如下所示：  
  
```  
public ref class Block {};         // reference class  
public value class Vector {};      // value class  
public interface class IFooBar {}; // interface class  
```  
  
## 將類別指定為抽象  
 在 Managed Extensions 中，您將關鍵字 `__abstract` 放在 `class` 關鍵字之前 \(可位於 `__gc` 的前後\)，來表示類別不完整，而且無法在程式中建立類別的物件：  
  
```  
public __gc __abstract class Shape {};  
public __gc __abstract class Shape2D: public Shape {};  
```  
  
 在新語法中，您可以在類別名稱之後以及類別主體、基底類別 \(Base Class\) 衍生清單或分號之前指定 `abstract` 內容關鍵字。  
  
```  
public ref class Shape abstract {};  
public ref class Shape2D abstract : public Shape{};  
```  
  
 而語意所代表的涵義當然還是一樣。  
  
## 將類別指定為密封  
 在 Managed Extensions 中，您將關鍵字 `__sealed` 放在 `class` 關鍵字之前 \(可位於 `__gc` 的前後\)，來表示無法從下列項目繼承類別的物件：  
  
```  
public __gc __sealed class String {};  
```  
  
 在新語法中，您可以在類別名稱之後以及類別主體、基底類別 \(Base Class\) 衍生清單或分號之前指定 `sealed` 內容關鍵字。  
  
 您可以衍生並且密封類別。  例如，`String` 類別會隱含衍生自 `Object`。  密封類別的優點是它可以透過密封參考類別物件，支援所有虛擬函式呼叫 \(Function Call\) 的靜態解析 \(亦即於編譯時期\)。  這是因為 `sealed` 規範保証 `String` 追蹤控制代碼無法參考後續的衍生類別，此類別可能會針對叫用的虛擬方法提供覆寫執行個體。  以下是使用新語法的密封類別範例：  
  
```  
public ref class String sealed {};  
```  
  
 您還可以將類別同時指定為抽象或密封，這是表示靜態類別的特殊情況。  這點會於 CLR 文件中詳細說明，如下所示：  
  
 「同時為 `abstract` 和 `sealed` 的型別只能具備靜態成員，而且在某些語言呼叫命名空間時使用。」  
  
 例如，下列是使用 Managed Extensions 語法所進行的抽象密封類別宣告：  
  
```  
public __gc __sealed __abstract class State {  
public:  
   static State() {}  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
 而下列是將這項宣告轉譯為新語法：  
  
```  
public ref class State abstract sealed {  
public:  
   static State();  
   static bool inParamList();  
  
private:  
   static bool ms_inParam;  
};  
```  
  
## CLR 繼承：指定基底類別  
 在 CLR 物件模型下，只支援公用單一繼承 \(Inheritance\)。  但是，Managed Extensions 會保留基底類別的 ISO\-C\+\+ 預設解譯，而不需存取關鍵字做為指定私用衍生之用。  這表示每項 CLR 繼承宣告都必須提供 `public` 關鍵字，以覆寫預設解譯。  
  
```  
// Managed Extensions: error: defaults to private derivation  
__gc class Derived : Base {};  
```  
  
 在新語法定義中，沒有存取關鍵字表示 CLR 繼承定義中有公用衍生，  因此，現在 `public` 存取關鍵字是選擇性的關鍵字。  雖然這並不需要在 Managed Extensions for C\+\+ 程式碼中進行任何修改，但在此處還是列出這項變更以求完整。  
  
```  
// New syntax: ok: defaults to public derivation  
ref class Derived : Base{};  
```  
  
## 請參閱  
 [Managed 類型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [abstract](../windows/abstract-cpp-component-extensions.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)