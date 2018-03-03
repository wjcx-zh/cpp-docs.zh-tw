---
title: "明確覆寫 （c + + 元件擴充功能） |Microsoft 文件"
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
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 346dd73952934d514b2741c41d5a27816b7152ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-overrides--c-component-extensions"></a>明確覆寫 (C++ 元件擴充功能)
本主題討論如何明確覆寫基底類別或介面的成員。 具名 （明確） 覆寫只應該用於覆寫具有名稱不同之衍生方法的方法。  
  
## <a name="all-runtimes"></a>所有執行階段  
 **語法**  
  
```  
  
      overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **參數**  
  
 *覆寫函式宣告子*  
 覆寫的函式的傳回類型、 名稱和引數清單。  請注意，覆寫的函式不需要有相同的名稱和覆寫的函式。  
  
 *type*  
 包含函式來覆寫基底類型。  
  
 *function*  
 若要覆寫的一或多個函式名稱的逗號分隔清單。  
  
 *覆寫函式定義*  
 定義覆寫的函式的函式主體陳述式。  
  
 **備註**  
  
 使用明確覆寫來建立別名方法簽章，或提供不同的實作方法 witht 相同的簽章的。  
  
 如需修改繼承型別和繼承的型別成員的行為的詳細資訊，請參閱[覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **備註**  
  
 明確的相關資訊會覆寫原生程式碼或程式碼使用編譯**/clr:oldSyntax**，請參閱[明確覆寫](../cpp/explicit-overrides-cpp.md)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 下列程式碼範例顯示簡單、 隱含覆寫和成員的實作在基底介面中，不使用明確覆寫。  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **輸出**  
  
```Output  
X::f override of I1::f  
```  
  
 **範例**  
  
 下列程式碼範例示範如何實作所有介面成員具有通用的簽章中，使用明確覆寫語法。  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **輸出**  
  
```Output  
X::f override of I1::f and I2::f  
X::f override of I1::f and I2::f  
```  
  
 **範例**  
  
 下列程式碼範例顯示如何函式覆寫可以有不同的名稱，從它所實作的函式。  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **輸出**  
  
```Output  
X::g  
```  
  
 **範例**  
  
 下列程式碼範例將示範實作型別安全的集合是明確介面實作。  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)