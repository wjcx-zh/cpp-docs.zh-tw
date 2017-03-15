---
title: "C 執行階段錯誤 R6002 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
caps.latest.revision: 10
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
ms.openlocfilehash: e9b50be6f1fd646f45ea1530c78e652f38b09c90
ms.lasthandoff: 02/24/2017

---
# <a name="c-runtime-error-r6002"></a>C 執行階段錯誤 R6002
未載入浮點支援  
  
 無法連結必要的浮點程式庫。  
  
> [!NOTE]
>  如果您執行應用程式時遇到此錯誤訊息，應用程式已關閉因為發生內部問題。 有幾個可能的原因，這個錯誤，但通常造成應用程式的程式碼的缺失，或嘗試執行的應用程式，並未建立特定的電腦處理器。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 這個錯誤可能在您的應用程式中的浮點程式庫無法連結。 請檢查這些原因的其中一個︰  
  
-   格式字串`printf_s`或`scanf_s`函式包含浮點格式規格，而且該程式未包含任何浮點值或變數。 若要修正此問題，使用浮點引數符合浮點格式規格，或是在程式中的其他地方執行浮點指派。 這會導致要載入浮點支援。  
  
-   編譯器會載入浮點支援只在必要時降低程式的大小。 編譯器無法偵測的浮點數運算或浮點格式規格在格式字串中，因此不會載入必要的浮點常式。 若要修正此問題，使用浮點格式規格和提供的浮點引數，或在程式中的其他地方執行浮點指派。 這會導致要載入浮點支援。  
  
-   在混合語言程式中，C 程式庫時所指定之前 FORTRAN 程式庫程式連結。 重新連結，最後指定 C 程式庫。
