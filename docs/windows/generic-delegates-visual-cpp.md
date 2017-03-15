---
title: "Generic Delegates (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic delegates"
  - "delegates, generic [C++]"
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Generic Delegates (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可使用具有委派的泛型型別參數  如需委派的詳細資訊，請參閱[delegate](../windows/delegate-cpp-component-extensions.md)。  
  
## 語法  
  
```  
[attributes]   
generic < [class | typename] type-parameter-identifiers >  
[type-parameter-constraints-clauses]  
[accessibility-modifiers] delegate result-type identifier   
([formal-parameters]);  
```  
  
#### 參數  
 `attributes` \(選擇性\)  
 補充宣告資訊。  如需關於屬性及屬性類別的詳細資訊，請參閱屬性。  
  
 *type\-parameter\-identifier\(s\)*  
 以逗號分隔的型別參數識別碼清單。  
  
 `type-parameter-constraints-clauses`  
 指定在 [Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../windows/constraints-on-generic-type-parameters-cpp-cli.md) 中拿到表格。  
  
 *存取範圍修飾詞* \(選擇性\)  
 Accessibility modifiers \(如  **public**，`private`\)。  
  
 *結果型別*  
 委派的傳回型別。  
  
 *identifier*  
 委派名稱。  
  
 *正規參數*\(選擇性\)  
 委派的參數清單。  
  
## 範例  
 委派型別參數指定於指標，而委派物件在此指標建立。  委派跟與其關聯的方法必須擁有相同的簽章。  以下為泛型委派的宣告範例。  
  
```  
// generics_generic_delegate1.cpp  
// compile with: /clr /c  
generic < class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
```  
  
## 範例  
 以下範例說明這點  
  
-   您不能使用相同的委派物件於不同的結構型別。  針對不同的型別建立不同的委派物件。  
  
-   泛型委派可以與泛型方法產生關聯。  
  
-   當呼叫泛型方法而沒有指定型別引數時，編譯器嘗試推斷出此呼叫的型別引數。  
  
```  
// generics_generic_delegate2.cpp  
// compile with: /clr  
generic < class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
  
generic < class ItemType>  
ref struct MyGenClass {  
   ItemType MyMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
ref struct MyClass {  
   generic < class ItemType>  
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
int main() {  
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();  
   GenDelegate<int>^ myDelegate1 =  
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   GenDelegate<double>^ myDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   GenDelegate<int>^ myDelegate =  
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);  
}  
```  
  
## 範例  
 下列範例宣告泛型委派`GenDelegate<ItemType>`，接著相關至使用型別參數`ItemType`的方法`MyMethod`來實作之。  創立並觸發（一個整數和一個雙數）的兩個委派實作個體。  
  
```  
// generics_generic_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare generic delegate  
generic <typename ItemType>  
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);  
  
// Declare a generic class:  
generic <typename ItemType>  
ref class MyGenClass {  
public:  
   ItemType MyMethod(ItemType p1, ItemType% p2) {  
      p2 = p1;  
      return p1;  
    }  
};  
  
int main() {  
   int i = 0, j = 0;   
   double m = 0.0, n = 0.0;  
  
   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();   
  
   // Instantiate a delegate using int.  
   GenDelegate<int>^ MyDelegate1 =   
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   i = MyDelegate1(123, j);  
  
   Console::WriteLine(  
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);  
  
   // Instantiate a delegate using double.  
   GenDelegate<double>^ MyDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   m = MyDelegate2(0.123, n);  
  
   Console::WriteLine(  
      "Invoking the double delegate: m = {0}, n = {1}", m, n);  
}  
```  
  
  **Invoking the integer delegate: i \= 123, j \= 123**  
**Invoking the double delegate: m \= 0.123, n \= 0.123**   
## 請參閱  
 [Generics](../windows/generics-cpp-component-extensions.md)