---
title: 如何： 使用 interior_ptr 關鍵字宣告實值型別 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 38cbfb171e218f70d45e5ef2e6e850d791803611
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571184"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>如何：使用 interior_ptr 關鍵字宣告實值類型 (C++/CLI)
**Interior_ptr**可以搭配實值型別。  
  
> [!IMPORTANT]
>  `/clr` 編譯器選項支援這項語言功能，`/ZW` 編譯器選項則不支援。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列 C + + /cli CLI 範例示範如何使用**interior_ptr**搭配實值類型。  
  
### <a name="code"></a>程式碼  
  
```cpp  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  
  
### <a name="output"></a>輸出  
  
```Output  
1  
2  
2  
3  
3  
3  
```  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 在實值型別**這**指標會判斷值為 interior_ptr。  
  
 實值型別的非靜態成員函式主體中`V`，**這**是類型的運算式`interior_ptr<V>`其值為，呼叫此函式物件的位址。  
  
### <a name="code"></a>程式碼  
  
```cpp  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例將示範如何使用具有靜態成員的傳址運算子。  
  
 靜態 Visual C++ 類型成員的位址會產生原生指標。  因為實值類型成員會配置在執行階段堆積上，而且可以由記憶體回收行程移動，所以靜態實值類型成員的位址是 Managed 指標。  
  
### <a name="code"></a>程式碼  
  
```cpp  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
### <a name="output"></a>輸出  
  
```Output 
22  
23  
hello  
```  
  
## <a name="see-also"></a>另請參閱  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)