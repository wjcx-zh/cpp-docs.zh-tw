---
title: "避免具有多執行緒程式的問題區域 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 546f5b5daa88578fc7dd062018257f0929bc0cff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>避免具有多執行緒程式的問題區域
有幾個建立、 連結或執行多執行緒 C 程式中可能會遇到的問題。 下表將說明一些較常見的問題。 (如從 MFC 的觀點的類似討論，請參閱[多執行緒： 程式設計提示](../parallel/multithreading-programming-tips.md)。)  
  
|問題|可能的原因|  
|-------------|--------------------|  
|您會取得在訊息方塊顯示您的程式造成保護違規。|許多 Win32 程式設計錯誤會造成保護違規。 保護違規的常見原因是間接指派到 null 指標的資料。 因為這會導致您的程式嘗試存取未隸屬於它的記憶體，就會發出保護違規。<br /><br /> 輕鬆地偵測保護違規的原因是編譯您的偵錯資訊的程式，然後將它執行透過 Visual c + + 環境中偵錯工具。 保護錯誤發生時，Windows 會將控制權傳輸至偵錯工具並造成問題的行，資料指標定位。|  
|您的程式會產生很多的編譯和連結錯誤。|您可以設定其最高值的其中一個編譯器的警告層級和留心警告訊息，以避免許多潛在的問題。 使用層級 3 或層級 4 警告層級的選項，您可以偵測不小心的資料轉換、 遺漏函式原型，並使用非 ANSI 功能。|  
  
## <a name="see-also"></a>請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)