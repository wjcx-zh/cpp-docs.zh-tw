---
title: "C 執行階段錯誤 R6002 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6652435425cdb04084d183987ea25be7c11114ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6002"></a>C 執行階段錯誤 R6002
未載入浮點支援  
  
 無法連結必要的浮點程式庫。  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有發生內部問題。 有幾個可能的原因，此錯誤，但它通常造成應用程式的程式碼缺失或嘗試執行未針對特定電腦處理器建置的應用程式。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 浮點數的程式庫無法連結時，可以在應用程式中發生此錯誤。 請檢查這些原因之一：  
  
-   格式字串`printf_s`或`scanf_s`函式包含浮點格式規格，而且該程式未包含任何浮點值或變數。 若要修正此問題，使用浮點引數為對應於浮點格式規格，或在程式中的其他地方執行浮點數指派。 這會導致要載入的浮點支援。  
  
-   編譯器會載入浮點支援只在必要時減少程式的大小。 編譯器無法偵測浮點運算或浮點格式規格格式字串中，所以無法載入必要的浮點常式。 若要修正此問題，使用浮點格式規格和提供的浮點引數，或在程式中的其他地方執行浮點數指派。 這會導致要載入的浮點支援。  
  
-   在混合語言程式中，C 程式庫之前 FORTRAN 文件庫時指定程式連結。 重新連結，並指定 C 程式庫上一次。