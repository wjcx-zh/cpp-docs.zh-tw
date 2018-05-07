---
title: 嚴重錯誤 C1900 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1900
dev_langs:
- C++
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da7cdd5601785f43748ec87d3219f43728536855
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1900"></a>嚴重錯誤 C1900
'Tool1' 版本 'number1' 與 'tool2' 版本 'number2' 之間的 Il 不符  
  
 在編譯器的不同階段中執行的工具不符。 ***number1***和***number2***檔案參考的日期。 例如，在階段 1，編譯器前端執行 (c1.dll)，而在階段 2 中，編譯器後端執行 (c2.dll)。 檔案上的日期必須相符。  
  
 若要修正這個問題，請確定所有的更新都已套用到 Visual Studio。 如果問題持續發生，請使用**程式和功能**Windows 控制台中修復或重新安裝 Visual Studio。