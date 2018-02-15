---
title: -CLRHEADER | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73f68c4f73d132254ea64d4b3b3b9f787f3a4b82
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="clrheader"></a>/CLRHEADER
```  
/CLRHEADER file  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `file`  
 使用建立的映像檔[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="remarks"></a>備註  
 CLRHEADER 顯示可用在任何受管理程式的.NET 標頭資訊。 輸出會顯示的位置和大小，以位元組為單位的.NET 標頭和標頭中的章節。  
  
 只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項僅適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。  
  
 /CLRHEADER 以 /clr 編譯的檔案上使用時，會有**clr 標頭：** dumpbin 輸出中的區段。  值**旗標**表示已使用哪一個 /clr 選項：  
  
-   0-/clr （映像可能包含原生程式碼）。  
  
 您也以程式設計方式可以檢查映像已針對 common language runtime。  如需詳細資訊，請參閱[How to： 判斷影像是否為原生或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。  
  
 **/Clr: pure**和**/clr: safe**編譯器選項在 Visual Studio 2015 中已被取代，以及編譯器的未來版本將移除。 必須是 「 單純的 」 或 「 安全 」 的程式碼應該移植到 C#。 
  
## <a name="see-also"></a>請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)