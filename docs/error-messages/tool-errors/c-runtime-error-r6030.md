---
title: C 執行階段錯誤 R6030 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae8eb17fc9d074604586582be08c43289b680b4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6030"></a>C 執行階段錯誤 R6030
未初始化的 CRT  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有發生內部問題。 這個問題是最常造成特定的安全性軟體程式，或很少，在程式中的 bug。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   您的安全性軟體可能會減少此問題的特定指示。 請檢查詳細資料的安全性軟體廠商的網站。 或者，檢查有更新版本的安全性軟體，或嘗試不同的安全性軟體。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 如果您使用 C 執行階段 (CRT)，但 CRT 啟始程式碼並未執行，就會發生此錯誤。 它是可能發生這個錯誤，如果連結器切換[/ENTRY](../../build/reference/entry-entry-point-symbol.md)用來覆寫預設的起始位址，通常**mainCRTStartup**， **wmainCRTStartup**的主控台 EXE 和**WinMainCRTStartup**或**wWinMainCRTStartup** Windows exe，或 **_DllMainCRTStartup** dll。 除非在啟動時，會呼叫其中一個上述函式，C 執行階段將不會初始化。 啟動呼叫這些函數通常根據預設，當您連結到 C 執行階段程式庫，並使用標準**主要**， **wmain**， **WinMain**，或**DllMain**進入點。  
  
 它也可另一個程式使用程式碼資料隱碼的技巧來攔截特定 DLL 程式庫呼叫時，發生這個錯誤。 某些具侵入性的安全性程式會使用這項技術。 在 Visual Studio 2015 之前的 Visual c + + 版本中，便可使用以靜態方式連結的 CRT 程式庫，若要解決此問題，但不是建議使用的安全性及應用程式更新的原因。 更正這個問題可能會需要使用者動作。