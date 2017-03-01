---
title: "C 執行階段錯誤 R6026 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6026
dev_langs:
- C++
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
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
ms.openlocfilehash: 2fee5ed771ce34ce8575f36ed4a14ad23532262e
ms.lasthandoff: 02/24/2017

---
# <a name="c-runtime-error-r6026"></a>C 執行階段錯誤 R6026
沒有足夠的空間 stdio 初始化  
  
> [!NOTE]
>  如果您執行應用程式時遇到此錯誤訊息，應用程式已關閉因為發生內部記憶體問題。 有幾個可能的原因，這個錯誤，但通常非常低的記憶體不足所引起。 此外，它也可能導致應用程式中的錯誤，它會使用，Visual c + + 程式庫損毀或驅動程式。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   關閉其他正在執行的應用程式或重新啟動電腦以釋放記憶體。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   如果應用程式所使用的另一個應用程式或驅動程式安裝之前，使用**應用程式和功能**或**程式和功能**頁面**控制台**移除新的應用程式或驅動程式，並再試一次您的應用程式。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**修復或重新安裝 Microsoft Visual c + + 可轉散發套件的所有複本。  
> -   檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 當沒有足夠的記憶體可用來初始化標準 I/O 支援中的 C 執行階段時，就會發生此錯誤。 在應用程式啟動時通常會發生此錯誤。 確認，您的應用程式的驅動程式和其所載入的 dll 進行不會損毀堆積在啟動時。
