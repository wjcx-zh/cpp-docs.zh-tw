---
title: 連結器工具錯誤 LNK1312 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1312
dev_langs:
- C++
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748276ed8fa459c41174f23d32bcef127cbdd510
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300442"
---
# <a name="linker-tools-error-lnk1312"></a>連結器工具錯誤 LNK1312
檔案無效或損毀： 無法匯入組件  
  
 建置組件、 模組或使用編譯的組件以外的檔案時 **/clr**傳遞給 **/ASSEMBLYMODULE**連結器選項。  如果您傳遞的物件檔 **/ASSEMBLYMODULE**，只要物件將直接傳遞至連結器，而不是以 **/ASSEMBLYMODULE**。  
  
## <a name="example"></a>範例  
 下列範例會建立.obj 檔案。  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK1312。  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```