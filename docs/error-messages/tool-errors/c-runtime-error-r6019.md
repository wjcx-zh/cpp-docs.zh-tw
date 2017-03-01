---
title: "C 執行階段錯誤 R6019 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
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
ms.openlocfilehash: 0a490fa1c15c3c2dc3285af6c69689c2a7fbd4b6
ms.lasthandoff: 02/24/2017

---
# <a name="c-runtime-error-r6019"></a>C 執行階段錯誤 R6019
無法開啟主控台裝置  
  
> [!NOTE]
>  如果您執行應用程式時遇到此錯誤訊息，應用程式已關閉，因為它嘗試存取主控台，但它並沒有足夠的權限。 有幾個可能的原因，這個錯誤，但通常是因為必須以系統管理員身分，執行程式或程式中有錯誤。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   以系統管理員身分執行程式。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 應用程式稱為主控台函式，但作業系統未授權存取主控台，就會發生此錯誤。 除了在偵錯模式中，主控台函式通常不允許在 Windows 市集應用程式。 如果您的應用程式需要系統管理員權限，才能執行，請確定它預設安裝到系統管理員身分執行。
