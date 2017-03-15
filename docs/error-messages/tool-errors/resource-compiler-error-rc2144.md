---
title: "資源編譯器錯誤 RC2144 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2144"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2144"
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資源編譯器錯誤 RC2144
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

PRIMARY LANGUAGE ID 不是數字  
  
 PRIMARY LANGUAGE ID 必須是十六進位語言 ID。  請參閱《執行階段程式庫參考》中的[語言和國家\/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)，以取得有效語言 ID 的清單。  
  
 如果已在 .RC 檔案中使用工具加入和刪除資源，也會發生此錯誤。  若要修正這個問題，請在文字編輯器中開啟 .RC 檔案，並以手動方式清除任何未使用的資源。