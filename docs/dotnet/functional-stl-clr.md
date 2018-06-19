---
title: 功能 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/functional>
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 38bfbe025c92aa54956a165367b367cecc6160b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112832"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)
包括 STL/CLR 標頭`<cliext/functional>`來定義範本類別和相關的範本委派函式的數目。  
  
## <a name="syntax"></a>語法  
  
```  
#include <functional>  
```  
  
## <a name="declarations"></a>宣告  
  
|Delegate - 委派|描述|  
|--------------|-----------------|  
|[binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)|兩個引數的委派。|  
|[binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)|傳回兩個引數委派`void`。|  
|[unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)|其中一個引數的委派。|  
|[unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)|傳回的單一引數委派`void`。|  
  
|類別|描述|  
|-----------|-----------------|  
|[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)|要變換正負號的雙引數函式的函式。|  
|[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)|若要將第一個引數繫結至兩個引數函式的函式。|  
|[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)|第二個引數繫結至兩個引數函式的函式。|  
|[divides (STL/CLR)](../dotnet/divides-stl-clr.md)|將多個函式。|  
|[equal_to (STL/CLR)](../dotnet/equal-to-stl-clr.md)|相等比較函式。|  
|[greater (STL/CLR)](../dotnet/greater-stl-clr.md)|大於比較仿函式。|  
|[greater_equal (STL/CLR)](../dotnet/greater-equal-stl-clr.md)|大於或等於比較仿函式。|  
|[less (STL/CLR)](../dotnet/less-stl-clr.md)|較少的比較函式。|  
|[less_equal (STL/CLR)](../dotnet/less-equal-stl-clr.md)|小於或等於比較仿函式。|  
|[logical_and (STL/CLR)](../dotnet/logical-and-stl-clr.md)|邏輯 AND 仿函式。|  
|[logical_not (STL/CLR)](../dotnet/logical-not-stl-clr.md)|邏輯不仿函式。|  
|[logical_or (STL/CLR)](../dotnet/logical-or-stl-clr.md)|邏輯 OR 仿函式。|  
|[minus (STL/CLR)](../dotnet/minus-stl-clr.md)|減去仿函式。|  
|[modulus (STL/CLR)](../dotnet/modulus-stl-clr.md)|模數仿函式。|  
|[multiplies (STL/CLR)](../dotnet/multiplies-stl-clr.md)|乘以仿函式。|  
|[negate (STL/CLR)](../dotnet/negate-stl-clr.md)|傳回否定其引數的函式。|  
|[not_equal_to (STL/CLR)](../dotnet/not-equal-to-stl-clr.md)|不等於比較仿函式。|  
|[plus (STL/CLR)](../dotnet/plus-stl-clr.md)|新增仿函式。|  
|[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)|要變換正負號的單一引數函式的函式。|  
  
|功能|描述|  
|--------------|-----------------|  
|[bind1st (STL/CLR)](../dotnet/bind1st-stl-clr.md)|會產生 binder1st 引數和函式。|  
|[bind2nd (STL/CLR)](../dotnet/bind2nd-stl-clr.md)|會產生 binder2nd 引數和函式。|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|會產生 unary_negate 函式的。|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|會產生 binary_negate 函式的。|  
  
## <a name="requirements"></a>需求  
 **標頭：** \<功能 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)