---
title: "C 執行階段錯誤 R6017 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 903d440dbedbe704ae28be643337619ca1e09c69
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="c-runtime-error-r6017"></a>C 執行階段錯誤 R6017
未預期的多執行緒鎖定錯誤  
  
> [!NOTE]
>  如果您執行應用程式時遇到此錯誤訊息，應用程式已關閉因為發生內部問題。 有幾個可能的原因，這個錯誤，但通常造成應用程式的程式碼缺失。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 處理程序嘗試存取系統資源上的 C 執行階段執行緒鎖定時，收到意外的錯誤。 如果處理序不慎更改執行階段堆積資料，通常會發生此錯誤。 然而，也可以是因為在執行階段程式庫或作業系統程式碼中的內部錯誤所造成。  
  
 若要修正這個問題，請檢查堆積損毀錯誤，程式碼中。 如需詳細資訊和範例，請參閱[CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。 接下來，請檢查您的應用程式部署使用最新的可轉散發套件。 如需資訊，請參閱[部署 Visual c + +](../../ide/deployment-in-visual-cpp.md)。
