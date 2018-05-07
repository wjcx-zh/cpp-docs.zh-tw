---
title: 編譯器錯誤 C3505 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3505
dev_langs:
- C++
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0ea8edd3237db2085365450f43b4b955d36f33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3505"></a>編譯器錯誤 C3505

> 無法載入類型程式庫 '*guid*'  
  
如果您正在執行 32 位元、 x86 裝載跨平台編譯器針對 64 位元，可能會造成 C3505，x64 64 位元上的目標電腦，因為編譯器會在 WOW64 下執行，且只可讀取的 32 位元登錄區。  
  
您可以藉由建置類型程式庫，您嘗試匯入，32 位元和 64 位元版本中解決此錯誤，然後再登錄兩者。  或者您可以使用原生的 64 位元編譯器需要您變更您**VC + + 目錄**指向的 64 位元編譯器在 IDE 中的屬性。  
  
如需詳細資訊，請參閱：  
  
-   [如何：在命令列啟用 64 位元 Visual C++ 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [如何：將 Visual C++ 專案設定成以 64 位元 x64 平台為目標](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)