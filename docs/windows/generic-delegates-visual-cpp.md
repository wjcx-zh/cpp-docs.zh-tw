---
title: "泛型委派 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2511034af4399c983b8114ec01a86e3290bd2a8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="generic-delegates-visual-c"></a>泛型委派 (Visual C++)
您可以使用具有委派的泛型型別參數。 如需委派的詳細資訊，請參閱[委派 （c + + 元件擴充功能）](../windows/delegate-cpp-component-extensions.md)。  
  
## <a name="syntax"></a>語法  
  
```  
[attributes]   
generic < [class | typename] type-parameter-identifiers >  
[type-parameter-constraints-clauses]  
[accessibility-modifiers] delegate result-type identifier   
([formal-parameters]);  
```  
  
#### <a name="parameters"></a>參數  
 `attributes`（選擇性）  
 其他宣告資訊。 如需關於屬性及屬性類別的詳細資訊，請參閱＜屬性＞。  
  
 *類型為參數的識別項*  
 以逗號分隔的型別參數識別項清單。  
  
 `type-parameter-constraints-clauses`  
 中指定的形式[泛型型別參數的條件約束 (C + + /CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *存取範圍修飾詞*（選擇性）  
 存取範圍修飾詞 (例如**公用**， `private`)。  
  
 *結果型別*  
 委派的傳回類型。  
  
 *identifier*  
 委派的名稱。  
  
 *正式參數*（選擇性）  
 委派的參數清單。  
  
## <a name="example"></a>範例  
 委派型別參數是在委派物件建立時指定。 委派以及與其相關聯的方法必須擁有相同的簽章。 以下為泛型委派宣告的範例。  
  
```  
// generics_generic_delegate1.cpp  
// compile with: /clr /c  
generic < class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
```  
  
## <a name="example"></a>範例  
 以下範例將示範  
  
-   您不能使用不同結構類型的相同委派物件。 為不同的類型建立不同的委派物件。  
  
-   泛型委派可以與泛型方法產生關聯。  
  
-   若呼叫泛型方法時沒有指定型別引數，則編譯器會嘗試推斷呼叫的型別引數。  
  
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
  
## <a name="example"></a>範例  
 下列範例會宣告泛型委派 `GenDelegate<ItemType>`，接著將它與使用類型參數 `MyMethod` 的方法 `ItemType` 產生關聯，藉此將它具現化。 將會建立並叫用委派的兩個執行個體 (一個整數和一個雙精度浮點數)。  
  
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
  
```Output  
Invoking the integer delegate: i = 123, j = 123  
Invoking the double delegate: m = 0.123, n = 0.123  
```  
  
## <a name="see-also"></a>請參閱  
 [泛型](../windows/generics-cpp-component-extensions.md)