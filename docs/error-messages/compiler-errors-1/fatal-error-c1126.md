---
title: 嚴重錯誤 C1126 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3ff02d69679074186e593d5e1c16bdf56d1052
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225910"
---
# <a name="fatal-error-c1126"></a>嚴重錯誤 C1126
'identifier': 自動配置超過大小  
  
 空間配置的本機變數之函式 （加上的編譯器，例如額外的 20 個位元組，可切換函式所使用的空間有限） 超過限制。  
  
 若要更正這個錯誤，請使用`malloc`或`new`配置大量的資料。