---
title: "連結器工具警告 LNK4075 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: 8
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
ms.sourcegitcommit: 9dee257bec0f09bd729bf10c4a1468ecb20dfa61
ms.openlocfilehash: 84dea754a1d2268c92e703dd04b0169ccc258ab3
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-warning-lnk4075"></a>連結器工具警告 LNK4075
忽略由於 「 option2 」 規格的 「 選項&1; 」  
  
 第二個選項會覆寫第一個。  
  
 會指定互斥的連結器選項。  檢查連結器選項。  連結器選項指定的位置取決於您如何建置您的專案。  
  
-   如果您要建置開發環境中，查看您的專案中的連結器屬性頁中，請參閱這兩個連結器選項所指定的位置。  請參閱[使用專案屬性](../../ide/working-with-project-properties.md)如需詳細資訊。  
  
-   如果您在命令列建置，請查看指定連結器選項。  
  
-   如果您使用建置指令碼來建置，請查看您的指令碼，請參閱這些連結器選項所指定的位置。  
  
 當您找到的互斥的連結器選項指定的位置時，請移除其中一個連結器選項。  
  
 某些特定的範例如下︰  
  
-   如果連結已編譯的模組**/ZI**，這表示由於 /opt，以及使用 /opt: ref、 /OPT:ICF 或 /incremental: no，已編譯的模組表示沒有由於 /opt 呼叫內部連結器選項，就會發生 LNK4075。  請參閱[/Z7、 /Zi、 /ZI （偵錯資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md)如需詳細資訊。
