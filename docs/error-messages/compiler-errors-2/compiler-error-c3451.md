---
title: "編譯器錯誤 C3451 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3451
dev_langs: C++
helpviewer_keywords: C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb68c546a9064801c68844039b7de077d5ee7c17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3451"></a>編譯器錯誤 C3451
'attribute': 無法套用 unmanaged 的屬性為 'type'  
  
 C + + 屬性無法套用至 CLR 型別。 請參閱[c + + 屬性參考](../../windows/cpp-attributes-reference.md)如需詳細資訊。  
  
 如需詳細資訊，請參閱 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致這個錯誤： [uuid](../../windows/uuid-cpp-attributes.md)屬性不再允許使用者定義的屬性，使用 CLR 程式設計上。 請改用 <xref:System.Runtime.InteropServices.GuidAttribute>。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3451。  
  
```  
// C3451.cpp  
// compile with: /clr /c  
using namespace System;  
[ attribute(AttributeTargets::All) ]  
public ref struct MyAttr {};  
  
[ MyAttr, helpstring("test") ]   // C3451  
// try the following line instead  
// [ MyAttr ]  
public ref struct ABC {};  
```