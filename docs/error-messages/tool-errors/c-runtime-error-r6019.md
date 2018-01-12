---
title: "C 執行階段錯誤 R6019 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6019
dev_langs: C++
helpviewer_keywords: R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c0e027907476eeacf10515556544160e402cd0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6019"></a>C 執行階段錯誤 R6019
無法開啟主控台裝置  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉，因為它嘗試存取主控台中，但它沒有足夠的權限。 有數個可能的原因，此錯誤，但通常是因為必須以系統管理員身分，執行程式，或有一個錯誤是在程式中。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   系統管理員身分執行程式。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 應用程式呼叫主控台函式，但作業系統未授與主控台的存取權，就會發生這個錯誤。 除了在偵錯模式中，主控台函式通常不允許在 Windows 市集應用程式。 如果您的應用程式需要系統管理員權限，才能執行，請確定它預設安裝到系統管理員身分執行。