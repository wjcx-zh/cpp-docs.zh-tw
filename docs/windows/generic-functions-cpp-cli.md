---
title: 泛型函式 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66eb27b28a1b18942c0a8a9a77a877a2f0b2ef8c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="generic-functions-ccli"></a>泛型函式 (C++/CLI)
泛型函式會宣告具有型別參數的函式。 呼叫時，會使用實際的類型，而不是型別參數。  
  
## <a name="all-platforms"></a>所有平台  
 **備註**  
  
 這項功能不適用於所有平台。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 **備註**  
  
 Windows 執行階段中不支援此功能。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 泛型函式會宣告具有型別參數的函式。 呼叫時，會使用實際的類型，而不是型別參數。  
  
 **語法**  
  
```  
[attributes] [modifiers]  
return-type identifier<type-parameter identifier(s)>  
[type-parameter-constraints clauses]  
  
([formal-parameters])  
{function-body}  
```  
  
 **參數**  
  
 *屬性*（選擇性）  
 其他宣告資訊。 如需有關屬性和屬性類別的詳細資訊，請參閱屬性。  
  
 *修飾詞*（選擇性）  
 對於函式，例如靜態修飾詞。  `virtual` 不允許因為虛擬方法不是泛型。  
  
 *傳回型別*  
 此方法傳回的型別。 如果傳回型別為 void，沒有傳回值需要。  
  
 *identifier*  
 函式名稱。  
  
 *型別參數的識別項*  
 以逗號分隔的識別項清單。  
  
 *正式參數*（選擇性）  
 參數清單。  
  
 *型別參數的條件約束子句*  
 這可做為型別引數，型別上指定的限制，並採用形式中指定[泛型型別參數的條件約束 (C + + /CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
 *函式主體*  
 可能會參考型別參數識別項的方法主體。  
  
 **備註**  
  
 泛型函式是以泛型型別參數宣告的函式。 可能是類別或結構或獨立的函式中的方法。 單一泛型宣告隱含宣告了一系列的差異只在於不同的實際類型為泛型型別參數的替代函式。  
  
 Visual c + + 類別或結構的建構函式不可以宣告具有泛型型別參數。  
  
 呼叫時，泛型型別參數取代為實際的類型。 使用類似於範本函式呼叫語法的角括號括住可明確指定實際的型別。 如果不使用型別參數呼叫，編譯器會嘗試推算函式呼叫中所提供的參數中的實際型別。 如果無法從使用的參數推論預定的型別引數，則編譯器會回報錯誤。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 下列程式碼範例示範泛型函式。  
  
```  
// generics_generic_function_1.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
ref struct A {  
   generic <typename ItemType>  
   void G(ItemType) {}  
  
   generic <typename ItemType>  
   static void H(int i) {}  
};  
  
int main() {  
   A myObject;  
  
   // generic function call  
   myObject.G<int>(10);  
  
   // generic function call with type parameters deduced  
   myObject.G(10);  
  
   // static generic function call  
   A::H<int>(10);  
  
   // global generic function call  
   G<int>(10);  
}  
```  
  
 **範例**  
  
 泛型函式可以根據簽章或引數數目、 函式的型別參數數目多載。 此外，泛型函式可以多載具有相同名稱的非泛型函式，只要在某些型別參數的函式不同。 例如，下列函式可以多載：  
  
```  
// generics_generic_function_2.cpp  
// compile with: /clr /c  
ref struct MyClass {  
   void MyMythod(int i) {}  
  
   generic <class T>   
   void MyMythod(int i) {}  
  
   generic <class T, class V>   
   void MyMythod(int i) {}  
};  
```  
  
 **範例**  
  
 下列範例會使用泛型函式，來尋找陣列中的第一個項目。 它會宣告`MyClass`，後者繼承自基底類別`MyBaseClass`。 `MyClass` 包含泛型函式， `MyFunction`，另一個泛型函式，呼叫`MyBaseClassFunction`，基底類別內。 在**主要**，泛型函式， `MyFunction`，使用不同的型別引數來呼叫。  
  
```  
// generics_generic_function_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyBaseClass {  
protected:  
   generic <class ItemType>  
   ItemType MyBaseClassFunction(ItemType item) {  
      return item;  
   }  
};  
  
ref class MyClass: public MyBaseClass {  
public:  
   generic <class ItemType>  
   ItemType MyFunction(ItemType item) {  
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);  
   }  
};  
  
int main() {  
   MyClass^ myObj = gcnew MyClass();  
  
   // Call MyFunction using an int.  
   Console::WriteLine("My function returned an int: {0}",  
                           myObj->MyFunction<int>(2003));  
  
   // Call MyFunction using a string.  
   Console::WriteLine("My function returned a string: {0}",  
   myObj->MyFunction<String^>("Hello generic functions!"));  
}  
```  
  
 **輸出**  
  
```Output  
My function returned an int: 2003  
My function returned a string: Hello generic functions!  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)   
 [泛型](../windows/generics-cpp-component-extensions.md)