---
title: 如何： 宣告原生類型中的控制代碼 |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
f1_keywords:
- gcroot
dev_langs:
- C++
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4573aac37eedecceab861eb41a70fc858b409fec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130967"
---
# <a name="how-to-declare-handles-in-native-types"></a>如何：以原生類型宣告控制代碼
您無法宣告原生類型中的控制代碼類型。 vcclr.h 提供類型安全包裝函式範本`gcroot`來參考 c + + 堆積的 CLR 物件。 此範本可讓您在原生類型中嵌入虛擬控制代碼，並將它視為基礎型別。 在大部分情況下，您可以使用`gcroot`物件做為內嵌類型，而不用任何轉型。 不過，在使用[針對每個，在](../dotnet/for-each-in.md)，您必須使用`static_cast`擷取基礎受管理的參考。  
  
 `gcroot`範本記憶體回收堆積中使用的實值類別 System::Runtime::InteropServices::GCHandle，提供 「 控制代碼 」 功能實作。 請注意，本身的控制代碼不是記憶體回收，並釋放時不在使用中的解構函式`gcroot`類別 （此解構函式無法呼叫以手動方式）。 如果您具現化`gcroot`物件到原生堆積上，您必須呼叫該資源上刪除。  
  
 執行階段會維護此控制代碼和它所參考的 CLR 物件之間的關聯。 當 CLR 物件移動時，記憶體回收堆積時，控制代碼會傳回物件的新位址。 變數沒有要指派給固定`gcroot`範本。  
  
## <a name="example"></a>範例  
 這個範例示範如何建立`gcroot`原生堆疊上的物件。  
  
```  
// mcpp_gcroot.cpp  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
class CppClass {  
public:  
   gcroot<String^> str;   // can use str as if it were String^  
   CppClass() {}  
};  
  
int main() {  
   CppClass c;  
   c.str = gcnew String("hello");  
   Console::WriteLine( c.str );   // no cast required  
}  
```  
  
```Output  
hello  
```  
  
## <a name="example"></a>範例  
 這個範例示範如何建立`gcroot`原生堆積上的物件。  
  
```  
// mcpp_gcroot_2.cpp  
// compile with: /clr  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
struct CppClass {  
   gcroot<String ^> * str;  
   CppClass() : str(new gcroot<String ^>) {}  
  
   ~CppClass() { delete str; }  
  
};  
  
int main() {  
   CppClass c;  
   *c.str = gcnew String("hello");  
   Console::WriteLine( *c.str );  
}  
```  
  
```Output  
hello  
```  
  
## <a name="example"></a>範例  
 這個範例示範如何使用`gcroot`保留在原生類型中的實值類型 （不是參考類型） 的參考，使用`gcroot`boxed 型別上。  
  
```  
// mcpp_gcroot_3.cpp  
// compile with: /clr  
#include < vcclr.h >  
using namespace System;  
  
public value struct V {  
   String^ str;  
};  
  
class Native {  
public:  
   gcroot< V^ > v_handle;  
};  
  
int main() {  
   Native native;  
   V v;  
   native.v_handle = v;  
   native.v_handle->str = "Hello";  
   Console::WriteLine("String in V: {0}", native.v_handle->str);  
}  
```  
  
```Output  
String in V: Hello  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)