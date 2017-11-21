---
title: "C 執行階段錯誤 R6025 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6025
dev_langs: C++
helpviewer_keywords: R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 06fd7aa6458a3c7e89d80146ec20a0e3f7587b4b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6025"></a>C 執行階段錯誤 R6025
純虛擬函式呼叫  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有發生內部問題。 此錯誤最常見的原因是在應用程式或安裝損毀的錯誤。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 沒有具有已具現化物件來處理純虛擬函式呼叫。  
  
 此錯誤的起因是抽象的基底類別，透過指標由衍生類別中的型別轉型，但實際上是基底類別的指標呼叫虛擬函式。 這可能是從轉型時**void\*** 類別的指標時**void\*** 基底類別的建構期間所建立。  
  
 如需詳細資訊，請參閱[Microsoft 支援服務](http://go.microsoft.com/fwlink/?LinkId=75220)網站。