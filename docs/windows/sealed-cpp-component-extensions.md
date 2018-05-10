---
title: 密封 （c + + 元件擴充功能） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05c75aef047e914086aaf4ae2c0d0d3bdd04e8c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="sealed--c-component-extensions"></a>sealed (C++ 元件擴充功能)
`sealed` 是表示不能覆寫虛擬成員、或類型不能用做基底類型的 ref 類別內容相關性關鍵字。  
  
> [!NOTE]
>  ISO C + + 11 標準語言有[最終](../cpp/final-specifier.md)支援 Visual Studio 中的關鍵字。 在標準類別上使用 `final` 而在 ref 類別上使用`sealed`。  
  
## <a name="all-runtimes"></a>所有執行階段  
  
## <a name="syntax"></a>語法
  
```  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
```  
  
### <a name="parameters"></a>參數  
  
 *identifier*  
 函式或類別的名稱。  
  
 *傳回型別*  
 由函數傳回的類型。  
  
## <a name="remarks"></a>備註  
  
 在第一個語法範例中，已密封類別。 在第二個範例中，已密封虛擬函式。  
  
 `sealed`關鍵字是有效的原生目標，以及 Windows 執行階段和 common language runtime (CLR)。 如需詳細資訊，請參閱[覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
 您可以在編譯時期偵測是否已密封類型使用`__is_sealed(type)`類型特性。 如需詳細資訊，請參閱[類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 `sealed` 是即時線上關鍵字。  如需詳細資訊，請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 請參閱[Ref 類別與結構](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 (這個語言功能沒有只適用於 Common Language Runtime 的備註。)  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 這個程式碼範例顯示 `sealed` 在虛擬成員上的效果。  
  
```cpp  
// sealed_keyword.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
   virtual void g();  
};  
  
ref class X : I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
  
   virtual void g() sealed {  
      System::Console::WriteLine("X::f override of I1::g");  
   }  
};  
  
ref class Y : public X {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("Y::f override of I1::f");  
   }  
  
   /*  
   // the following override generates a compiler error  
   virtual void g() override {  
      System::Console::WriteLine("Y::g override of I1::g");  
   }    
   */  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
   MyI -> g();  
  
   I1 ^ MyI2 = gcnew Y;  
   MyI2 -> f();  
}  
```  
  
```Output  
X::f override of I1::f  
X::f override of I1::g  
Y::f override of I1::f  
```  
  
 下一步的程式碼範例示範如何將類別標示為已密封。  
  
```cpp  
// sealed_keyword_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X sealed : I1 {  
public:  
   virtual void f() override {}  
};  
  
ref class Y : public X {   // C3246 base class X is sealed  
public:  
   virtual void f() override {}  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)