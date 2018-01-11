---
title: "literal （c + + 元件擴充功能） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- literal
- literal_cpp
dev_langs: C++
helpviewer_keywords: literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f858e94bf916c2d441cee607739bb9e08da09b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="literal-c-component-extensions"></a>literal (C++ 元件擴充功能)
變數 （資料成員） 標示為`literal`中**/clr**編譯相當於原生的`static const`變數。  
  
## <a name="all-platforms"></a>所有平台  
 **備註**  
  
 (這個語言功能沒有適用所有執行階段的備註。)  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 **備註**  
  
 (這個語言功能沒有只適用於 Windows 執行階段的備註。)  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
  
## <a name="remarks"></a>備註  
 資料成員標記為`literal`必須在宣告時初始化和值必須是常數的整數類資料類型、 列舉或字串類型。 從初始化運算式的類型轉換成靜態常數資料成員的類型時，不可要求使用者定義的轉換。  
  
 在執行階段不會為常值欄位配置記憶體，編譯器只會在類別的中繼資料內插入其值。  
  
 標記為 `static const` 的變數將不會在中繼資料內提供給其他編譯器。  
  
 如需詳細資訊，請參閱[靜態](../cpp/storage-classes-cpp.md)和[const](../cpp/const-cpp.md)。  
  
 `literal` 是即時線上關鍵字。 請參閱[即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 這個範例將示範 `literal` 變數表示 `static`。  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## <a name="example"></a>範例  
 下列範例將示範中繼資料內常值的影響：  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 請注意 `sc` 和 `lit` 之中繼資料內的差異：`modopt` 指示詞會套用至 `sc`，這表示其他編譯器可以忽略它。  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## <a name="example"></a>範例  
 下列範例是以 C# 撰寫，會參考先前範例中建立的中繼資料，並顯示 `literal` 和 `static const` 變數的影響：  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)