---
title: 嚴重錯誤 C1046 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1046
dev_langs:
- C++
helpviewer_keywords:
- C1046
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 02c609d5f846fa6f339eac98b725919560df068f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1046"></a>嚴重錯誤 C1046
編譯器限制： 結構巢狀太深  
  
 結構、 等位或類別超過巢狀的限制為 15 層級。 請重寫的定義，以減少巢狀層級。 使用中將結構、 等位或類別分割成兩個或多個部分`typedef`定義一個或多個巢狀結構。