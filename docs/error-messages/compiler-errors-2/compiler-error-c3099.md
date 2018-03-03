---
title: "編譯器錯誤 C3099 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3099
dev_langs:
- C++
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a644a27c834efcd3c3857241927a6e618f600d0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3099"></a>編譯器錯誤 C3099
'keyword': 對 Managed 屬性使用 [System::AttributeUsageAttribute]；對 WinRT 屬性使用 [Windows::Foundation::Metadata::AttributeUsageAttribute]  
  
 使用<xref:System.AttributeUsageAttribute>宣告**/clr**屬性。 使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 宣告 Windows 執行階段屬性。  
  
 如需 /CLR 屬性的詳細資訊，請參閱[使用者定義的屬性](../../windows/user-defined-attributes-cpp-component-extensions.md)。 支援 Windows 執行階段中的屬性，請參閱[Windows.Foundation.Metadata 命名空間](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
## <a name="example"></a>範例  
 下列範例會產生 C3099，並示範如何修正此問題。  
  
```  
// C3099.cpp  
// compile with: /clr /c  
using namespace System;  
[usage(10)]   // C3099  
// try the following line instead  
// [AttributeUsageAttribute(AttributeTargets::All)]  
ref class A : Attribute {};  
```