---
title: "連結器工具錯誤 LNK1104 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
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
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 7fce9c60da4bceafb9ee81231a8630acb4397d83
ms.lasthandoff: 04/24/2017

---
# <a name="linker-tools-error-lnk1104"></a>連結器工具錯誤 LNK1104
無法開啟檔案 '*filename*'  
  
連結器無法開啟指定的檔案。  
  
若要修正這個錯誤，請檢查下列可能原因︰  
  
-   檔案*filename*不存在。 如果您的專案相依於另一個專案來產生這個檔案，請確定已正確設定您的專案相依性。  
  
-   指定程式庫的專案屬性頁 對話方塊中，當程式庫名稱必須是以空格分隔，不是逗號。  
  
-   檔案名稱或命令列上指定的路徑不正確，或包含無效的磁碟機規格。 檢查拼字，並確認檔案名稱和位置。 如果您要建置的專案，從另一部電腦複製，請檢查路徑[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)和必要時更新它們。  
  
-   不會安裝的程式庫的專案組態或平台工具組。 請確認的平台工具組和 Windows SDK 為您的專案屬性頁面中指定已安裝，且包含的工具組和組態設定所需的程式庫。 有不同的偵錯和零售組態設定，因此如果其中一個建置的運作方式，但其他會導致錯誤，請確定設定正確，而且這兩種設定已安裝必要的工具。  
  
-   您沒有足夠的磁碟空間。 不尋常的連結器在連結期間會耗用大量的暫存磁碟空間。  
  
-   您有檔案權限不足以存取*filename*。  
  
-   路徑*filename*超過 260 個字元。 變更名稱，或重新排列您的目錄結構，如有需要可縮短必要檔案的路徑。  
  
-   如果*filename*名為 LNK*n*、 連結器為暫存檔所產生的檔案名稱、 TMP 環境變數中指定的目錄可能不存在，或為 TMP 環境變數可指定多個目錄。 只有一個目錄路徑應指定為 TMP 環境變數。  
  
-   如果錯誤訊息是因某程式庫名稱而出現，且您最近才移植了一個舊版 Microsoft Visual C++ 開發系統的 .mak 檔，該程式庫可能不再有效。 請確認程式庫名稱正確，且仍然存在於指定的位置，或更新 LIB 路徑以指向新位置。  
  
-   其他程式可能開啟該檔案，而使連結器無法寫入。 防毒程式經常會暫時封鎖新建立的檔案的存取權。 請嘗試將專案組建目錄排除防毒掃描程式。  
  
-   您有不正確的 LIB 環境變數。 如需如何更新 LIB 環境變數的資訊，請參閱[VC + + 目錄屬性頁](../../ide/vcpp-directories-property-page.md)。 請確定您所需之程式庫的任何目錄皆列於此處。  
  
-   連結器在幾種情況下會使用暫存檔。 即使您有足夠的磁碟空間，非常大型的連結可以耗盡或片段的可用磁碟空間。 請考慮使用[/editandcontinue （最佳化）](../../build/reference/opt-optimizations.md)選項; 執行可轉移的 comdat 刪除讀取所有目的檔多次。
