---
title: 編譯器警告 （層級 1） C4376 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4376
dev_langs:
- C++
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 615faaaa586e60a32ce670cd554a8b0b1c157a25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4376"></a>編譯器警告 (層級 1) C4376
存取規範 'old_specifier:' 不再支援： 請使用' new_specifier:' 改為  
  
 如需有關如何指定型別和成員可存取性中繼資料中的詳細資訊，請參閱[類型可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[成員可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)中[如何： 定義和使用類別和結構 (C + + CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).  
  
## <a name="example"></a>範例  
 下列範例會產生 C4376。  
  
```  
// C4376.cpp  
// compile with: /clr /W1 /c  
public ref class G {  
public public:   // C4376  
   void m2();  
};  
  
public ref class H {  
public:   // OK  
   void m2();  
};  
```