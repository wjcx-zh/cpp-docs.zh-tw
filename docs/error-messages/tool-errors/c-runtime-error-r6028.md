---
title: C 執行階段錯誤 R6028 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b978d1d9165fd48be9d0ce31aa72092fc660dbd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297819"
---
# <a name="c-runtime-error-r6028"></a>C 執行階段錯誤 R6028
無法初始化堆積  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有內部記憶體問題。 有許多原因會造成這個錯誤，但它通常造成極低記憶體的情況，在程式中的 bug 或損壞的硬體驅動程式。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   關閉其他正在執行的應用程式或重新啟動電腦以釋放記憶體。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   如果應用程式所使用的另一個應用程式或驅動程式安裝之前，使用**應用程式和功能**或**程式和功能**頁面**控制台**移除新的應用程式或驅動程式，然後再試一次您的應用程式。  
> -   請檢查硬體廠商的網站或**Windows Update**中**控制台**軟體和驅動程式更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 當作業系統無法為應用程式建立記憶體集區時，便會發生這個錯誤。 特別是，C 執行階段 (CRT) 會呼叫 Win32 函式 `HeapCreate`，該函式會傳回表示錯誤的 NULL。  
  
 如果在應用程式啟動時發生這個錯誤，系統可能因為載入了不良的驅動程式而無法滿足堆積要求。 請查看 Windows Update 或硬體廠商的網站是否有更新的驅動程式。