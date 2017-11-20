---
title: "原生類型中的巢狀之實值類型的版本問題 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __nogc type declarations
- __value keyword, issues when nesting
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a16b6fd7d166b7a997257bfd6cb741b82911c5bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="version-issues-for-value-types-nested-in-native-types-ccli"></a>在原生類型中巢狀化之實值類型的版本問題 (C++/CLI)
請考慮用來建置用戶端組件的帶正負號 （強式名稱） 組件元件。 元件包含在用戶端當做類型使用的原生的等位、 類別或陣列成員的實值類型。 如果未來版本的元件變更的大小或實值類型的配置，用戶端必須重新編譯。  
  
 建立與 keyfile [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`)。  
  
## <a name="example"></a>範例  
 下列範例是的元件。  
  
```  
// nested_value_types.cpp  
// compile with: /clr /LD  
using namespace System::Reflection;  
[assembly:AssemblyVersion("1.0.0.*"),   
assembly:AssemblyKeyFile("mykey.snk")];  
  
public value struct S {  
   int i;  
   void Test() {  
      System::Console::WriteLine("S.i = {0}", i);  
   }  
};  
```  
  
## <a name="example"></a>範例  
 這個範例是用戶端：  
  
```  
// nested_value_types_2.cpp  
// compile with: /clr  
#using <nested_value_types.dll>  
  
struct S2 {  
   S MyS1, MyS2;  
};  
  
int main() {  
   S2 MyS2a, MyS2b;  
   MyS2a.MyS1.i = 5;  
   MyS2a.MyS2.i = 6;  
   MyS2b.MyS1.i = 10;  
   MyS2b.MyS2.i = 11;  
  
   MyS2a.MyS1.Test();  
   MyS2a.MyS2.Test();  
   MyS2b.MyS1.Test();  
   MyS2b.MyS2.Test();  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### <a name="comments"></a>註解  
 不過，如果您將加入另一個成員`struct S`中 nested_value_types.cpp，(比方說， `double d;`) 和重新編譯此元件不需要重新編譯用戶端，結果是未處理的例外狀況 (型別<xref:System.IO.FileLoadException?displayProperty=fullName>)。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 類型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)