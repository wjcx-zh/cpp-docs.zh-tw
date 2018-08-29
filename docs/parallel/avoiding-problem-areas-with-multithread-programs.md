---
title: 避免具有多執行緒程式的問題區域 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97a69c52adb5094c7c7841a93b73b1a83cd786d9
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131058"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>避免具有多執行緒程式的問題區域
有幾個建立、 連結，或執行多執行緒 C 程式中可能會遇到的問題。 下表將說明一些更常見的問題。 (從 MFC 的觀點來看類似的討論，請參閱[多執行緒： 程式設計提示](multithreading-programming-tips.md)。)  
  
|問題|可能的原因|  
|-------------|--------------------|  
|您取得在訊息方塊顯示您的程式造成保護違規。|許多 Win32 程式設計錯誤會導致保護違規。 保護違規的常見原因是間接的資料指派給 null 指標。 因為這會導致程式嘗試存取不屬於它的記憶體，就會發出保護違規。<br /><br /> 輕鬆地偵測保護違規的原因是編譯您的程式與偵錯資訊，然後透過在 Visual c + + 環境中偵錯工具中執行它。 保護錯誤發生時，Windows 會將控制權傳輸至偵錯工具和資料指標定位造成該問題的那一行。|  
|您的程式會產生許多編譯和連結的錯誤。|您可以設定其最高值的其中一個編譯器的警告層級和留心警告訊息，以避免許多潛在的問題。 使用層級 3 或層級 4 警告層級選項，您可以偵測非預期的資料轉換、 遺漏的函式原型，並使用非 ANSI 功能。|  
  
## <a name="see-also"></a>另請參閱  

[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)