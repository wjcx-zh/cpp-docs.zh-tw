---
title: "-GENPROFILE，FASTGENPROFILE （產生程式碼剖析檢測的建置） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 028b31044d035def628785969a04c27af4699f65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE、/FASTGENPROFILE (產生程式碼剖析檢測建置)
指定連結器產生的 .pgd 檔，以支援特性指引最佳化 (PGO)。  /GENPROFILE 和 /FASTGENPROFILE 使用不同的預設參數。 在程式碼剖析期間，使用 /GENPROFILE 讓精確度優先於速度和記憶體使用量。 使用 /FASTGENPROFILE 讓較小的記憶體使用量和速度優先於精確度。  
  
## <a name="syntax"></a>語法  
  
```  
/{GENPROFILE|FASTGENPROFILE}[:{COUNTER32|COUNTER64|EXACT|MEMMAX=#|MEMMIN=#|NOEXACT|NOPATH|NOTRACKEH|PATH|PGD=filename|TRACKEH}]   
```  
  
## <a name="remarks"></a>備註  
 COUNTER32 &#124;COUNTER64  
 使用 COUNTER32 指定使用 32 位元的探查計數器，使用 COUNTER64 指定使用 64 位元的探查計數器。 當您指定 /GENPROFILE 時，預設值為 COUNTER64。 當您指定 /FASTGENPROFILE 時，預設值為 COUNTER32。  
  
 確切 &#124;NOEXACT  
 使用 EXACT 指定探查使用安全執行緒連鎖遞增。 NOEXACT 指定探查使用不受保護的遞增作業。 預設值是 NOEXACT。  
  
 MEMMAX=value，MEMMIN=value  
 使用 MEMMAX 和 MEMMIN 指定記憶體中訓練資料的最大和最小保留大小。 值是以位元組為單位的要保留記憶體數量。  這些值預設由內部的啟發學習法決定。  
  
 路徑 &#124;NOPATH  
 使用 PATH 為函式的每個唯一路徑另外指定一組 PGO 計數器。 使用 NOPATH 為每個函式只指定一組計數器。   當您指定 /GENPROFILE 時，預設值為 PATH。 當您指定 /FASTGENPROFILE 時，預設值為 NOPATH。  
  
 TRACKEH &#124;NOTRACKEH  
 指定在訓練期間擲回例外狀況時，是否使用額外的計數器來保持精確的計數。 使用 TRACKEH 為確切的計數指定額外的計數器。 使用 NOTRACKEH 指定程式碼的單一計數器，這段程式碼不使用例外狀況處理或不會碰到訓練情節的例外狀況。  當您指定 /GENPROFILE 時，預設值為 TRACKEH。 當您指定 /FASTGENPROFILE 時，預設值為 NOTRACKEH。  
  
 PGD=filename  
 指定 .pgd 檔的主檔名。 連結器預設使用副檔名為 .pgd 的可執行影像主檔名。  
  
 /GENPROFILE 和 /FASTGENPROFILE 選項會告知連結器產生需要的程式碼剖析檢測檔案，以支援用於特性指引最佳化 (PGO) 的應用程式訓練。 應用程式訓練所產生的程式碼剖析資訊用做輸入，在建置期間執行整個程式的最佳化。   您可以設定其他選項，在應用程式訓練和建置期間控制各種效能的程式碼剖析功能。 /GENPROFILE 指定的預設選項會提供最精確的結果，特別是針對大型且複雜的多執行緒應用程式。 /FASTGENPROFILE 選項會使用不同的預設值在訓練期間取得較低的記憶體耗用量和更快的效能，但會犧牲精確度。  
  
 當您使用 /FASTGENPROFILE 的 /GENPROFILE 在建置之後執行已檢測的應用程式時，會擷取到程式碼分析資訊。 當您指定 /USEPROFILE 選項時，連結器會使用這項資訊。 如需如何訓練應用程式及有關收集資料明細的詳細資訊，請參閱＜特性指引最佳化＞。  
  
 當您指定 /GENPROFILE 或 /FASTGENPROFILE 時也必須指定 /LTCG。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md)