---
title: "嚴重錯誤 C1126 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1126
dev_langs: C++
helpviewer_keywords: C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4f5346a3adb5535242207ebc3a3c9b2fcffa7a40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1126"></a>嚴重錯誤 C1126
'identifier': 自動配置超過大小  
  
 空間配置的本機變數之函式 （加上的編譯器，例如額外的 20 個位元組，可切換函式所使用的空間有限） 超過限制。  
  
 若要更正這個錯誤，請使用`malloc`或`new`配置大量的資料。