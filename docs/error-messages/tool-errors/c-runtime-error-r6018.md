---
title: C 執行階段錯誤 R6018 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6018
dev_langs:
- C++
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4946e3a8341963ee1a1ca2c3ad65d64cfbad8080
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6018"></a>C 執行階段錯誤 R6018
未預期的堆積錯誤  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有發生內部問題。 有數個可能的原因，此錯誤，但通常它在應用程式的程式碼的缺失所引發。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 程式執行記憶體管理作業時，發生未預期的錯誤。  
  
 如果程式不小心變更執行階段堆積資料，通常會發生這個錯誤。 不過，它也可能會因執行階段或作業系統的程式碼中發生內部錯誤。  
  
 若要修正此問題，請檢查堆積損毀錯誤程式碼中。 如需詳細資訊和範例，請參閱[CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。 接下來，檢查使用最新的可轉散發套件為您的應用程式部署。 如需資訊，請參閱[部署 Visual c + +](../../ide/deployment-in-visual-cpp.md)。