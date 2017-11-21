---
title: "C 執行階段錯誤 R6016 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6016
dev_langs: C++
helpviewer_keywords: R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 10bac18ac50b67037e855e4f25e067afd0cb34ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6016"></a>C 執行階段錯誤 R6016
執行緒資料空間不足  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有內部記憶體問題。 有許多原因會造成這個錯誤，但它通常造成極低記憶體的情況，應用程式中的 bug 或增益集或應用程式使用的擴充功能中的 bug。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   關閉其他正在執行的應用程式或重新啟動電腦以釋放記憶體。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**修復或重新安裝應用程式。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**移除，請修復或重新安裝增益集或應用程式使用的擴充功能。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 因為程式未從才能完成作業系統收到足夠的記憶體，就會發生此錯誤[_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)或`_beginthreadex`呼叫，或是執行緒區域儲存區尚未初始化所`_beginthread`或`_beginthreadex`。  
  
 當新的執行緒啟動時，程式庫必須為執行緒建立一個內部資料庫。 當使用作業系統提供的記憶體無法展開資料庫時，執行緒就無法啟動，呼叫的處理序也會停止。 當處理序已建立過多執行緒，或是執行緒區域儲存區已用盡時，就會發生這種情形。  
  
 我們建議您呼叫 C 執行階段程式庫 (CRT) 的可執行檔應該使用`_beginthreadex`執行緒的建立，而不是 Windows API `CreateThread`。 `_beginthreadex` 會初始化執行緒區域儲存區中許多 CRT 函式所使用的內部靜態儲存區。 如果您使用 `CreateThread` 建立執行緒，則呼叫需要已初始化的內部靜態儲存區的 CRT 函式時，CRT 可能會終止處理序並發出 R6016。