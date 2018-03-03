---
title: "連結至 ATL 專案中 CRT |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DllMainCRTStartup
- wWinMainCRTStartup
- WinMainCRTStartup
dev_langs:
- C++
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 631426fece3960303d67d8929e99c404beaab998
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>連結到該 CRT，在您的 ATL 專案
[C 執行階段程式庫](../c-runtime-library/crt-library-features.md)(CRT) 提供許多有用的函式可讓程式設計工作更輕鬆在 ATL 開發期間。 所有的 ATL 專案將連結到 CRT 程式庫。 您可以看到連結中的方法的優缺點[優點和權衡取捨的方法用來連結到該 CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md)。  
  
## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>連結到 CRT 的程式映像上的效果  
 如果您以靜態方式連結到該 CRT，CRT 的程式碼會在您可執行檔映像中，您不需要執行您的映像的系統上有 CRT DLL。 如果您以動態方式連結到該 CRT，CRT DLL 中的程式碼的參考會放置在您的映像，但不是程式碼本身。 為了讓您指定的系統上執行的映像，必須是該系統上有 CRT DLL。 即使當您以動態方式連結到 CRT 的資訊，您可能會發現某些程式碼可以以靜態方式連結 (例如， **DllMainCRTStartup**)。  
  
 當您連結您的映像時，您明確或隱含指定的作業系統會在載入映像之後呼叫的進入點。 預設進入點的 DLL、 **DllMainCRTStartup**。 EXE，對於**WinMainCRTStartup**。 您可以覆寫使用 /ENTRY 連結器選項的預設值。 提供的實作，CRT **DllMainCRTStartup**， **WinMainCRTStartup**，和**wWinMainCRTStartup** （Unicode 進入點的 EXE）。 這些 CRT 提供進入點的全域物件上呼叫建構函式，並初始化有些 CRT 函式所使用的其他資料結構。 啟始程式碼會將大約 25 K 加入至您的映像中，如果它以靜態方式連結。 如果動態連結，大部分的程式碼位於 DLL，讓您的映像大小會維持小。  
  
 如需詳細資訊，請參閱連結器主題[/ENTRY （進入點符號）](../build/reference/entry-entry-point-symbol.md)。  
  
## <a name="optimization-options"></a>最佳化選項  
 使用連結器選項 /OPT:NOWIN98 可以進一步減少 10k，預設 ATL 控制項損失的增加載入 Windows 98 系統上的時間。 如需有關連結選項的詳細資訊，請參閱[/editandcontinue （最佳化）](../build/reference/opt-optimizations.md)。  
  
## <a name="see-also"></a>請參閱  
 [ATL 和 C 執行階段程式碼的程式設計](../atl/programming-with-atl-and-c-run-time-code.md)   
 [DLL 和 Visual C++ 執行階段程式庫行為](../build/run-time-library-behavior.md)

