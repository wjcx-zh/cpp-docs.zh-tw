---
title: "虛擬目標 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 761b71f05840c86516563df79d45cc1bb018fbba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pseudotargets"></a>虛擬目標
虛擬目標是用來取代在相依的檔案名稱的標籤。 將它解譯為不存在，且為已過期的檔案。 NMAKE 假設虛擬目標的時間戳記是最新的所有相依性。 如果不有任何相依項目，則會假設目前的時間。 如果虛擬目標做為目標，一律執行它的命令。 虛擬目標做為相依性也必須出現為其他相依性中的目標。 不過，該相依性不需要有命令區塊。  
  
 虛擬目標名稱遵循目標檔名語法規則。 不過，如果名稱未具備擴充功能 （亦即，不包含句號），它可以超過 8 個字元限制的檔名，而且可以是最多 256 個字元。  
  
## <a name="see-also"></a>請參閱  
 [目標](../build/targets.md)