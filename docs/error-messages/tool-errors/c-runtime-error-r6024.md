---
title: C 執行階段錯誤 R6024 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6024
dev_langs:
- C++
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcdfee9da378415afe0b88fe6eed18ec8f570d4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302707"
---
# <a name="c-runtime-error-r6024"></a>C 執行階段錯誤 R6024
_onexit/atexit 資料表空間不足  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有內部記憶體問題。 此錯誤原因通常是由非常低記憶體情況，或很少，程式中的錯誤或損毀，它會使用的 Visual c + + 程式庫。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   關閉其他正在執行的應用程式或重新啟動電腦以釋放記憶體。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**修復或重新安裝 Microsoft Visual c + + 可轉散發套件的所有複本。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 因為不沒有可用的任何記憶體，會發生這個錯誤`_onexit`或`atexit`函式。 這個錯誤被因記憶體不足的狀況。 您可以考慮在低記憶體情形的預先配置的緩衝區，可協助將使用者資料儲存及執行全新的應用程式的應用程式啟動時結束。