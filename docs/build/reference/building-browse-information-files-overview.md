---
title: "建置瀏覽資訊檔： 概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f5b369d5a708e0ee56df635234c68ee88a31af48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="building-browse-information-files-overview"></a>建置瀏覽資訊檔：概觀
若要建立的符號瀏覽資訊時，編譯器會建立每個來源檔案的.sbr 檔案在您的專案，然後 BSCMAKE。EXE 會串連成一個.bsc 檔案的.sbr 檔案。  
  
 產生.sbr 和.bsc 檔案需要時間，因此 Visual c + + 會關閉這些函式，根據預設。 如果您想要瀏覽目前的資訊，您必須開啟瀏覽選項，並再次建置您的專案。  
  
 使用[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)或[/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)告訴編譯器建立的.sbr 檔案。 若要建立.bsc 檔案，您可以呼叫[BSCMAKE](../../build/reference/bscmake-command-line.md)從命令列。 從命令列使用 BSCMAKE，讓您更精確地控制瀏覽資訊檔的操作。 請參閱[BSCMAKE 參考](../../build/reference/bscmake-reference.md)如需詳細資訊。  
  
> [!TIP]
>  您可以開啟.sbr 檔案產生，但請勿關閉.bsc 檔產生。 這提供快速建置，但也可讓您快速建立全新的.bsc 檔，所產生的.bsc 檔開啟和建置專案。  
  
 您可以減少時間、 記憶體和磁碟空間才能建置.bsc 檔藉由減少.bsc 檔的大小。  
  
 請參閱[一般屬性頁 （專案）](../../ide/general-property-page-project.md)如需有關如何建立在開發環境中的瀏覽器檔案資訊。  
  
### <a name="to-create-a-smaller-bsc-file"></a>若要建立較小的.bsc 檔案  
  
1.  使用[BSCMAKE 命令列選項](../../build/reference/bscmake-options.md)排除瀏覽資訊檔的資訊。  
  
2.  略過一或多個.sbr 檔時編譯，或組合中的本機符號。  
  
3.  如果物件檔案沒有偵錯的程式目前階段所需的資訊，請省略 BSCMAKE 命令從其.sbr 檔案，當您重建瀏覽資訊檔。  
  
### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>若要瀏覽資訊結合數個專案成一個瀏覽資訊檔 (.bsc)  
  
1.  請不要建置.bsc 檔，在專案層級，或使用 /n 參數來防止.sbr 檔被截斷。  
  
2.  所有專案都建置後，請與所有.sbr 檔案都執行 BSCMAKE，做為輸入。 使用萬用字元。 比方說，如果您在專案目錄 C:\X、 C:\Y 和 C:\Z 以及您想要將它們合併成一個.bsc 檔所有.sbr 檔案，然後使用 BSCMAKE C:\X\\*.sbr C:\Y\\\*.sbr C:\Z\\\*。sbr /o c:\whatever_directory\combined.bsc 建置結合的.bsc 檔案。  
  
## <a name="see-also"></a>請參閱  
 [C/c + + 建置工具](../../build/reference/c-cpp-build-tools.md)   
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)