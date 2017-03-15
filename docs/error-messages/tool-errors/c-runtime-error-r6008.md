---
title: "C 執行階段錯誤 R6008 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7ff8749859bd9f0300a606c7cc5e328873fe1f5c
ms.lasthandoff: 02/24/2017

---
# <a name="c-runtime-error-r6008"></a>C 執行階段錯誤 R6008
引數的空間不足  
  
> [!NOTE]
>  如果您執行應用程式時遇到此錯誤訊息，應用程式已關閉因為發生內部記憶體問題。 有幾個可能的原因，這個錯誤，但通常極低的記憶體不足，環境變數或在程式中的 bug 所太多記憶體所造成。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   關閉其他正在執行的應用程式或重新啟動電腦以釋放記憶體。  
> -   減少應用程式的數目和大小的命令列引數。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 發生記憶體不足，無法載入程式，但沒有足夠的記憶體來建立**argv**陣列。 這可能造成極低記憶體情況，或是異常大的命令列或環境變數的使用方式。 請考慮下列解決方案之一︰  
  
-   增加可用程式記憶體數量。  
  
-   減少的數目和大小的命令列引數。  
  
-   減少環境大小，藉由移除不必要的變數。
