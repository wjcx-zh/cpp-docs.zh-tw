---
title: "連結器工具錯誤 LNK1312 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1312
dev_langs: C++
helpviewer_keywords: LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d7f7b57512f58402403a50bf57176f975769573
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1312"></a>連結器工具錯誤 LNK1312
檔案無效或損毀： 無法匯入組件  
  
 建置組件、 模組或使用編譯的組件以外的檔案時**/clr**傳遞給**/ASSEMBLYMODULE**連結器選項。  如果您傳遞的物件檔**/ASSEMBLYMODULE**，只要物件將直接傳遞至連結器，而不是以**/ASSEMBLYMODULE**。  
  
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