---
title: "嚴重錯誤 C1510 |Microsoft 文件"
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1510
dev_langs:
- C++
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d4128580facdc87239d0087fef1cf9eff701854
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1510"></a>嚴重錯誤 C1510
無法開啟語言資源 clui.dll  
  
 編譯器無法載入語言資源 DLL。  
  
有兩個常見的原因，此問題。 使用 32 位元編譯器和工具時，您可能會看到此錯誤在大型專案，在連結時使用超過 2 GB 的記憶體。 在 64 位元 Windows 系統上可能的解決方案是使用 64 位元原生或跨編譯器和工具來產生程式碼。 這會利用較大的記憶體空間供 64 位元應用程式。 如果您必須使用 32 位元編譯器，因為您執行 32 位元系統上，在某些情況下您可以增加至連結器 3 gb 的可用記憶體數量。 如需詳細資訊，請參閱[4 Gb 微調： BCDEdit 和 Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473(v=vs.85).aspx)和[BCDEdit /set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx)命令。  

其他常見的原因是 Visual Studio 安裝損毀或不完整。 在此情況下，執行一次來修復或重新安裝 Visual Studio 安裝程式。  
  