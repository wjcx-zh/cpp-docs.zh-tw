---
title: "C 執行階段錯誤 R6027 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6027
dev_langs: C++
helpviewer_keywords: R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 080b5cdf2e68889e7d11fe14f20524f9cced03c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6027"></a>C 執行階段錯誤 R6027
沒有足夠的空間 lowio 初始化  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息時執行的應用程式時，應用程式已關閉因為它有內部記憶體問題。 有數個可能的原因，此錯誤，但通常非常低的記憶體所引起。 此外，它也可能造成應用程式中的錯誤、 損毀，它所使用的 Visual c + + 程式庫或驅動程式。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   關閉其他正在執行的應用程式或重新啟動電腦以釋放記憶體。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**來修復或重新安裝程式。  
> -   如果應用程式所使用的另一個應用程式或驅動程式安裝之前，使用**應用程式和功能**或**程式和功能**頁面**控制台**移除新的應用程式或驅動程式，然後再試一次您的應用程式。  
> -   使用**應用程式和功能**或**程式和功能**頁面**控制台**修復或重新安裝 Microsoft Visual c + + 可轉散發套件的所有複本。  
> -   請檢查**Windows Update**中**控制台**軟體更新。  
> -   檢查應用程式的更新版本。 如果此問題持續發生，請連絡應用程式廠商。  
  
 **程式設計人員的資訊**  
  
 當沒有足夠的可用記憶體可用來初始化 C 執行階段中的低階 I/O 支援時，就會發生此錯誤。 此錯誤通常是在應用程式啟動。 請確認，您的應用程式的驅動程式和其所載入的 dll 執行不會損毀在啟動堆積。