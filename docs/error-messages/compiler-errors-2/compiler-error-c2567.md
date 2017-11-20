---
title: "編譯器錯誤 C2567 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2567
dev_langs: C++
helpviewer_keywords: C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bbdc535f75230da05a92eb0498176da40e918ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2567"></a>編譯器錯誤 C2567
無法開啟 'file' 中的中繼資料，檔案可能已刪除或移動  
  
 已在來源中參考的中繼資料檔案 (與`#using`) 找不到相同的目錄中由編譯器後端處理序的編譯器前端程序。 請參閱[#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)如需詳細資訊。  
  
 如果您使用編譯時，可能造成 C2567 **/c**上一個機器，然後在另一部電腦上的連結時間程式碼產生。 如需詳細資訊，請參閱[/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md))。  
  
 它也可能表示您的電腦已經沒有多餘的記憶體。  
  
 若要更正這個錯誤，請確定中繼資料檔案是在相同的目錄位置的所有階段建置程序。