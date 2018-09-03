---
title: C 執行階段錯誤 R6008 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d32734850c58b64694e96c3a27b759131e6c5ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299873"
---
# <a name="c-runtime-error-r6008"></a>C 執行階段錯誤 R6008
引數的空間不足  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有內部記憶體問題。 有數個可能的原因，此錯誤，但通常非常低記憶體的情況，太多記憶體，由環境變數或在程式中的 bug 所造成。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   關閉其他正在執行的應用程式或重新啟動電腦以釋放記憶體。  
> -   減少應用程式的數目和大小的命令列引數。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 時發生記憶體不足，無法載入程式，但沒有足夠的記憶體來建立**argv**陣列。 這可能被造成極低記憶體情況，或是非常大的命令列或環境變數的使用方式。 請考慮下列解決方案之一：  
  
-   增加可用程式記憶體數量。  
  
-   減少的數量和大小的命令列引數。  
  
-   移除不必要的變數，以減少環境大小。