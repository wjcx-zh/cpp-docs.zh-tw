---
title: 嚴重錯誤 C1905 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1905
dev_langs:
- C++
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d15bf00432cab6900c252d85cd642c414bdbbb22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199427"
---
# <a name="fatal-error-c1905"></a>嚴重錯誤 C1905
前端和後端不相容 (必須以相同處理器為目標)  
  
 當 .obj 檔是由專門處理 x86、ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 這類處理器的編譯器前端 (C1.dll) 產生，但卻由專門處理不同處理器的後端 (C2.dll) 讀取時，就會產生這項錯誤。  
  
 若要修正這個問題，請確定您使用相符的前端和後端。 這是在 Visual Studio 中所建立專案的預設值。 如果您有編輯專案檔，並使用編譯器工具的不同路徑，可能會發生這個錯誤。 如果您沒有特別設定編譯器工具的路徑，則如果您的 Visual Studio 安裝已損毀，就可能會發生這個錯誤。 比方說，您可能將編譯器 .dll 檔案由一個位置複製到另一個位置。 使用**程式和功能**Windows 控制台中修復或重新安裝 Visual Studio。