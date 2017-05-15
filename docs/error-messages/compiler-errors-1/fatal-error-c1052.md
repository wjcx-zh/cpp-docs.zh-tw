---
title: "嚴重錯誤 C1052 |Microsoft 文件"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1052
dev_langs:
- C++
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
caps.latest.revision: 0
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: f3ab91c1c79b822a4d9a33fb0ab5fbd88146fff0
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="fatal-error-c1052"></a>嚴重錯誤 C1052
程式資料庫檔案 '*filename*'，所產生連結器使用 /debug: fastlink; 編譯器無法更新這類 PDB 檔案; 請將它刪除或使用 /Fd 指定其他 PDB 檔案名稱  
  
編譯器無法更新由連結器所產生的相同程式資料庫 (PDB) 檔案時[/debug: fastlink](../../build/reference/debug-generate-debug-info.md)指定選項。 通常編譯器所產生 PDB 檔和連結器產生的 PDB 檔案具有不同的名稱。 不過，如果它們會設定為使用相同的名稱，可以產生這個錯誤。  
  
若要修正此問題，您可以明確 PDB 檔案之前刪除您編譯一次，或者您可以建立不同的編譯器產生和連結器產生的 PDB 檔案名稱。 若要在命令列建立不同的編譯器產生 PDB 檔案名稱，請使用[/Fd](../../build/reference/fd-program-database-file-name.md)選項。 若要在 IDE 中產生不同的 PDB 檔案名稱，請開啟**屬性頁**對話方塊，您的專案，然後在**組態屬性**， **C/c + +**，**輸出檔**頁面上，設定**程式資料庫檔名**屬性。 根據預設，這個屬性是`$(IntDir)vc$(PlatformToolsetVersion).pdb`。 或者，您可以設定連結器產生的 PDB 檔案名稱。 開啟**屬性頁**對話方塊，您的專案，然後在**組態屬性**，**連結器**，**偵錯**頁面上，設定**產生程式資料庫檔**屬性。 根據預設，這個屬性設定為`$(OutDir)$(TargetName).pdb`。  

