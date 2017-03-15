---
title: "functional (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "<cliext/functional>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/functional> 標頭 [STL/CLR]"
  - "<functional> 標頭 [STL/CLR]"
  - "functional 函式 [STL/CLR]"
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# functional (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含 STL\/CLR 標頭 `<cliext/functional>` 定義多個樣板類別和相關範本委派和函式。  
  
## 語法  
  
```  
#include <functional>  
```  
  
## 宣告  
  
|委派|說明|  
|--------|--------|  
|[binary\_delegate](../dotnet/binary-delegate-stl-clr.md)|兩個引數的委派。|  
|[binary\_delegate\_noreturn](../dotnet/binary-delegate-noreturn-stl-clr.md)|傳回 `void`的兩個引數的委派。|  
|[unary\_delegate](../dotnet/unary-delegate-stl-clr.md)|單一引數委派。|  
|[unary\_delegate\_noreturn](../dotnet/unary-delegate-noreturn-stl-clr.md)|傳回 `void`的一個引數的委派。|  
  
|類別|說明|  
|--------|--------|  
|[binary\_negate](../dotnet/binary-negate-stl-clr.md)|否定兩個引數功能中的功能\)。|  
|[binder1st](../dotnet/binder1st-stl-clr.md)|繫結至第一個引數的功能會對兩個引數的功能。|  
|[binder2nd](../dotnet/binder2nd-stl-clr.md)|繫結至第二個引數的功能會對兩個引數的功能。|  
|[divides](../dotnet/divides-stl-clr.md)|刪除功能。|  
|[equal\_to](../dotnet/equal-to-stl-clr.md)|相等比較子功能。|  
|[greater](../dotnet/greater-stl-clr.md)|較大的比較子功能。|  
|[greater\_equal](../dotnet/greater-equal-stl-clr.md)|大於或等於比較子功能。|  
|[less](../dotnet/less-stl-clr.md)|較少比較子功能。|  
|[less\_equal](../dotnet/less-equal-stl-clr.md)|小於或等於比較子功能。|  
|[logical\_and](../dotnet/logical-and-stl-clr.md)|邏輯 AND 功能。|  
|[logical\_not](../dotnet/logical-not-stl-clr.md)|邏輯 NOT 功能。|  
|[logical\_or](../dotnet/logical-or-stl-clr.md)|邏輯功能 OR 工具。|  
|[minus](../dotnet/minus-stl-clr.md)|減去的功能。|  
|[模數](../dotnet/modulus-stl-clr.md)|模數功能。|  
|[multiplies](../dotnet/multiplies-stl-clr.md)|乘功能。|  
|[negate](../dotnet/negate-stl-clr.md)|傳回其引數的功能的相反。|  
|[not\_equal\_to](../dotnet/not-equal-to-stl-clr.md)|不相等比較子功能。|  
|[plus](../dotnet/plus-stl-clr.md)|新增功能。|  
|[unary\_negate](../dotnet/unary-negate-stl-clr.md)|否定一個引數功能中的功能。|  
  
|功能|說明|  
|--------|--------|  
|[bind1st](../dotnet/bind1st-stl-clr.md)|產生給引數和功能子的 binder1st 。|  
|[bind2nd](../dotnet/bind2nd-stl-clr.md)|產生給引數和功能子的 binder2nd 。|  
|[not1](../dotnet/not1-stl-clr.md)|產生功能工具的 unary\_negate。|  
|[not1](../dotnet/not1-stl-clr.md)|產生功能工具的 binary\_negate。|  
  
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)