---
title: "C 執行階段錯誤 R6017 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6017
dev_langs: C++
helpviewer_keywords: R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 57345feed2044683a1d5fd2a6ee7d14c412a827d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6017"></a>C 執行階段錯誤 R6017
未預期的多執行緒鎖定錯誤  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有發生內部問題。 有數個可能的原因，此錯誤，但通常它在應用程式的程式碼的缺失所引發。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 處理程序嘗試存取系統資源上的 C 執行階段執行緒鎖定時，收到未預期的錯誤。 如果處理程序不小心變更執行階段堆積資料，通常會發生這個錯誤。 不過，它也可能會因執行階段程式庫或作業系統的程式碼中發生內部錯誤。  
  
 若要修正此問題，請檢查堆積損毀錯誤程式碼中。 如需詳細資訊和範例，請參閱[CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。 接下來，檢查使用最新的可轉散發套件為您的應用程式部署。 如需資訊，請參閱[部署 Visual c + +](../../ide/deployment-in-visual-cpp.md)。