---
title: "typeid （c + + 元件擴充功能） |Microsoft 文件"
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
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 20a3b1153bbb8a8502a54aa74998817abf191860
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="typeid--c-component-extensions"></a>typeid (C++ 元件擴充功能)
取得值，指出物件類型。  
  
> [!WARNING]
>  本主題是指 typeid 的 C++ 元件擴充功能版本。 此關鍵字 ISO c + + 版本，請參閱[typeid 運算子](../cpp/typeid-operator.md)。  
  
## <a name="all-runtimes"></a>所有執行階段  
  
### <a name="syntax"></a>語法  
  
```cpp  
T::typeid  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 類型名稱。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
  
### <a name="syntax"></a>語法  
  
```cpp  
Platform::Type^ type = T::typeid;  
```  
  
### <a name="parameters"></a>參數  
 `T`  
 類型名稱。  
  
### <a name="remarks"></a>備註  
 在 C + + /CX 中，typeid 會傳回[platform:: type](../cppcx/platform-type-class.md) ，從執行階段類型資訊所建構。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **語法**  
  
```  
  
type::typeid  
```  
  
 **參數**  
  
 *type*  
 要 system:: type 物件的類型 （抽象宣告子） 的名稱。  
  
 **備註**  
  
 `typeid`用來取得<xref:System.Type>在編譯時期的類型。  
  
 `typeid`類似於在執行的階段使用的型別取得 system:: type<xref:System.Type.GetType%2A>或<xref:System.Object.GetType%2A>。 不過，typeid 只會接受型別名稱做為參數。  如果您想要取得其 system:: type 名稱中使用類型的執行個體，使用 GetType。  
  
 `typeid`必須是能夠在編譯時期評估型別名稱 （類型），而 GetType 評估在執行階段傳回的型別。  
  
 `typeid`可以採用原生型別名稱或通用語言執行階段別名的原生型別名稱。請參閱[c + + 原生類型的.NET Framework 對等用法 (C + + /CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)如需詳細資訊。  
  
 `typeid`雖然它仍會傳回 system:: type，也可以搭配原生類型。  若要取得 type_info 結構，請使用[typeid 運算子](../cpp/typeid-operator.md)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 下列範例會比較 typeid 關鍵字 gettype （） 成員。  
  
```  
// keyword__typeid.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   Type ^ pType = pG->GetType();  
   Type ^ pType2 = G::typeid;  
  
   if (pType == pType2)  
      Console::WriteLine("typeid and GetType returned the same System::Type");  
   Console::WriteLine(G::typeid);  
  
   typedef float* FloatPtr;  
   Console::WriteLine(FloatPtr::typeid);  
}  
```  
  
 **輸出**  
  
```Output  
typeid and GetType returned the same System::Type  
G  
  
System.Single*  
  
```  
  
 **範例**  
  
 下列範例會顯示 system:: type 可以用來取得型別上的屬性類型的變數。  它也會顯示，針對某些類型，您必須建立使用 typedef `typeid`。  
  
```  
// keyword__typeid_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
typedef int ^ handle_to_int;  
typedef int * pointer_to_int;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass {  
public:  
   AtClass(Type ^) {  
      Console::WriteLine("in AtClass Type ^ constructor");  
   }  
};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass2 {  
public:  
   AtClass2() {  
      Console::WriteLine("in AtClass2 constructor");  
   }  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
ref class B : Attribute {};  
  
int main() {  
   Type ^ MyType = B::typeid;  
  
   Console::WriteLine(MyType->IsClass);  
  
   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);  
   for (int i = 0 ; i < MyArray->Length ; i++ )  
      Console::WriteLine(MyArray[i]);  
  
   if (int::typeid != pointer_to_int::typeid)  
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");  
  
   if (int::typeid == handle_to_int::typeid)  
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");  
}  
```  
  
 **輸出**  
  
```Output  
True  
  
in AtClass2 constructor  
  
in AtClass Type ^ constructor  
  
AtClass2  
  
System.AttributeUsageAttribute  
  
AtClass  
  
int::typeid != pointer_to_int::typeid, as expected  
  
int::typeid == handle_to_int::typeid, as expected  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)