---
title: "嚴重錯誤 C1382 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1382
dev_langs: C++
helpviewer_keywords: C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 923cc957dd136147a6c749f5ebf9508ca7e2052d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1382"></a>嚴重錯誤 C1382
已經重建 PCH 檔案 'file'，因為已產生 'obj'。 請重建此物件  
  
 當使用[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)，編譯器偵測到較指到該 CIL.obj 的.pch 檔案。 CIL.obj 檔案中的資訊已過期。 重建物件。  
  
 如果您使用編譯也會發生 C1382 **/Yc**，但也多個來源的程式碼將檔案傳遞給編譯器。  若要解決，請勿使用**/Yc**時將多個來源的程式碼檔案傳遞至編譯器。  如需詳細資訊，請參閱[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)。