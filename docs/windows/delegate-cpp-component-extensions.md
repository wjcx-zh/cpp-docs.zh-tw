---
title: "delegate （c + + 元件擴充功能） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- delegate_cpp
- delegate
dev_langs: C++
helpviewer_keywords: delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 30fd64fd37fb30c34b5d4f5901f16143fb1cd701
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="delegate--c-component-extensions"></a>delegate (C++ 元件擴充功能)
宣告表示函式指標的類型。  
  
## <a name="all-runtimes"></a>所有執行階段  
 Windows 執行階段和通用語言執行平台支援委派。  
  
### <a name="remarks"></a>備註  
 `delegate` 是即時線上關鍵字。 如需詳細資訊，請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
 若要在編譯時期偵測類型是否為委派，使用`__is_delegate()`類型特性。 如需詳細資訊，請參閱[類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 C + + /CX 支援使用下列語法的委派。  
  
### <a name="syntax"></a>語法  
  
```cpp  
access  
delegate  
return-type  
delegate-type-identifier  
(  
[ parameters ]  
)  
  
```  
  
### <a name="parameters"></a>參數  
 *access*  
 （選擇性）委派，它可以是的協助工具`public`（預設值） 或`private`。 函式原型也可以以限定`const`或`volatile`關鍵字。  
  
 *傳回型別*  
 函式原型的傳回型別。  
  
 *委派類型識別碼*  
 宣告的委派類型的名稱。  
  
 *參數*  
 （選擇性）類型和函式原型的識別項。  
  
### <a name="remarks"></a>備註  
 使用*委派類型識別碼*來宣告事件和委派的相同原型。 如需詳細資訊，請參閱[委派 (C + + /CX)](../cppcx/delegates-c-cx.md)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 Common language runtime 支援使用下列語法的委派。  
  
### <a name="syntax"></a>語法  
  
```cpp  
access  
delegate  
function_declaration  
  
```  
  
### <a name="parameters"></a>參數  
 *access*  
 （選擇性）委派外部組件的存取範圍可以是公用或私用。  預設為私用。  類別、 委派可以有任何存取範圍。  
  
 *function_declaration*  
 可以繫結至委派的函式簽章。 委派的傳回型別可以是任何 managed 型別。 互通性考量，建議委派的傳回型別是 CLS 類型。  
  
 若要定義繫結的委派的第一個參數*function_declaration*應該是類型`this`物件的指標。 
  
### <a name="remarks"></a>備註  
 委派是多點傳送: 「 函式指標 」 可以繫結 managed 類別內的一或多個方法。 **委派**關鍵字會定義特定的方法簽章的多點傳送的委派類型。  
  
 委派也繫結至方法的實值類別，例如靜態方法。  
  
 委派具有下列特性：  
  
-   它繼承自**system:: multicastdelegate**。  
  
-   它有兩個引數的建構函式： managed 類別的指標或**NULL** （如果是繫結至靜態方法） 以及所指定型別的完整限定的方法。  
  
-   它擁有稱為 `Invoke` 的方法，其簽章與宣告的委派簽章相符。  
  
 叫用委派時，其函式會呼叫它們所附加的順序。  
  
 委派的傳回值是從其最後一個附加的成員函式傳回的值。  
  
 委派不可多載。  
  
 委派可以繫結或未繫結。  
  
 當您具現化的繫結的委派時，第一個引數應該是物件參考。  委派具現化的第二個引數必須是實值類型的方法是方法的 managed 的類別物件或指標的位址。   委派具現化的第二個引數必須以完整類別的範圍語法方法，並套用傳址運算子。  
  
 當您具現化未繫結的委派時，第一個引數應該是 managed 的類別物件或方法的實值類型的指標的方法的位址。   引數必須以完整類別的範圍語法方法，並套用傳址運算子。  
  
 建立靜態或全域函式委派，當只有一個參數是必要項： 函式 （或者，函式的位址）。  
  
 如需委派的詳細資訊，請參閱  
  
-   [如何：定義和使用委派 (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)  
  
-   [泛型委派 (Visual C++)](../windows/generic-delegates-visual-cpp.md)  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 下列範例會示範如何宣告、 初始化及叫用委派。  
  
```cpp  
// mcppv2_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare a delegate  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      Console::WriteLine("in func1 {0}", i);  
   }  
  
   void func2(int i) {  
      Console::WriteLine("in func2 {0}", i);  
   }  
  
   static void func3(int i) {  
      Console::WriteLine("in static func3 {0}", i);  
   }  
};  
  
int main () {  
   A ^ a = gcnew A;  
  
   // declare a delegate instance  
   MyDel^ DelInst;  
  
   // test if delegate is initialized  
   if (DelInst)  
      DelInst(7);  
  
   // assigning to delegate  
   DelInst = gcnew MyDel(a, &A::func1);  
  
   // invoke delegate  
   if (DelInst)  
      DelInst(8);  
  
   // add a function  
   DelInst += gcnew MyDel(a, &A::func2);  
  
   DelInst(9);  
  
   // remove a function  
   DelInst -= gcnew MyDel(a, &A::func1);  
  
   // invoke delegate with Invoke  
   DelInst->Invoke(10);  
  
   // make delegate to static function  
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);  
   StaticDelInst(11);  
}  
```  
  
 **輸出**  
  
```Output  
in func1 8  
  
in func1 9  
  
in func2 9  
  
in func2 10  
  
in static func3 11  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)