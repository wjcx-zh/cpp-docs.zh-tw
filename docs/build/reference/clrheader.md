---
title: "-CLRHEADER |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /CLRHEADER
dev_langs: C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d8ab1617cffd7560ab47d69f7304df0c76b661eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
-   1--/clr: safe （映像為唯一，能夠執行任何 CLR 平台上，可能是可驗證的 MSIL）。  
  
-   3--/clr: pure (映像只有 MSIL，但只可以在 x86 上執行的平台)。  
  
 您也以程式設計方式可以檢查映像已針對 common language runtime。  如需詳細資訊，請參閱[How to： 判斷影像是否為原生或 CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
## <a name="see-also"></a>請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)