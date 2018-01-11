---
title: "連結器工具警告 LNK4075 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4075
dev_langs: C++
helpviewer_keywords: LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8c3330e637ae0e0dce5e875fcc349c6deefcf27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4075"></a>連結器工具警告 LNK4075
忽略"1"由於"選項 2"規格  
  
 第二個選項會覆寫第一個。  
  
 互斥連結器選項所指定。  請檢查連結器選項。  連結器選項指定的位置取決於您如何建置您的專案。  
  
-   如果您要建置在開發環境中，查看您專案的連結器屬性頁，並請參閱其中這兩個連結器選項所指定。  請參閱[使用專案屬性](../../ide/working-with-project-properties.md)如需詳細資訊。  
  
-   如果您在命令列建置時，看看那里指定的連結器選項。  
  
-   如果您建立與建置指令碼，請查看您的指令碼，以查看其中這些連結器選項所指定。  
  
 當您找到的互斥連結器選項指定的位置時，請移除其中一個連結器選項。  
  
 某些特定的範例：  
  
-   如果您將連結與已編譯的模組**/ZI**，這表示內部連結器選項呼叫 /EDITANDCONTINUE，以及 /opt: ref，/opt: icf 或 /incremental: no，編譯的模組表示沒有 /EDITANDCONTINUE，您將會取得 LNK4075。  請參閱[/Z7、 /Zi、 /ZI （偵錯資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md)如需詳細資訊。