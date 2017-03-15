---
title: "建置瀏覽資訊檔：概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".bsc 檔案, 關於 .bsc 檔案"
  - "瀏覽資訊檔 (.bsc)"
  - "瀏覽資訊檔 (.bsc), 建立"
  - "bsc 檔案, 關於 bsc 檔案"
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 建置瀏覽資訊檔：概觀
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為了建立瀏覽符號用的瀏覽資訊，編譯器會為專案中的每個原始程式檔建立一個 .sbr 檔，接著 BSCMAKE.EXE 會將 .sbr 檔連結成一個 .bsc 檔。  
  
 產生 .sbr 及 .bsc 檔會需要一些時間，因此預設情形下 Visual C\+\+ 是將這些功能關閉的。  如果您希望瀏覽目前的資訊，必須開啟瀏覽選項並重建您的專案。  
  
 使用 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) 或 [\/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)，指示編譯器建立 .sbr 檔。  若要建立 .bsc 檔，您可以從命令列呼叫 [BSCMAKE](../../build/reference/bscmake-command-line.md)。  從命令列使用 BSCMAKE，讓您可以對瀏覽資訊檔的管理擁有更精確的控制。  如需詳細資訊，請參閱 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)。  
  
> [!TIP]
>  您可以將 .sbr 檔產生功能開啟，但是讓 .bsc 檔產生功能保持關閉，  如此便可快速地進行建置，而且也讓您能夠透過開啟 .bsc 檔產生功能並建置專案，快速地建立全新的 .bsc 檔。  
  
 藉由減少 .bsc 檔的大小，您就可以減少建置 .bsc 檔所需的時間、記憶體和磁碟空間。  
  
 如需如何在開發環境中建置瀏覽資訊檔 \(Browser File\) 的詳細資訊，請參閱[一般屬性頁 \(專案\)](../../ide/general-property-page-project.md)。  
  
### 若要建立較小的 .bsc 檔  
  
1.  使用 [BSCMAKE 命令列選項](../../build/reference/bscmake-options.md)，從瀏覽資訊檔中排除資訊。  
  
2.  編譯或組譯時，省略一或多個 .sbr 檔中的區域符號。  
  
3.  如果目的檔 \(Object File\) 中不包含目前偵錯階段所需的資訊，當您重建瀏覽資訊檔時，可以在 BSCMAKE 命令中省略它的 .sbr 檔。  
  
### 若要將數個專案的瀏覽資訊結合於一個瀏覽資訊檔 \(.bsc\) 中  
  
1.  不在專案等級建置 .bsc 檔或是使用 \/n 參數，來防止 .sbr 檔被截斷。  
  
2.  在所有專案都已建置後，以所有的 .sbr 檔做為輸入來執行 BSCMAKE。  可以接受萬用字元。  例如，如果您有 C:\\X、C:\\Y 和 C:\\Z 專案目錄，其中都有 .sbr 檔，您希望將這些 .sbr 檔結合到一個 .bsc 檔中，可以使用 BSCMAKE C:\\X\\\*.sbr C:\\Y\\\*.sbr C:\\Z\\\*.sbr \/o c:\\whatever\_directory\\combined.bsc 來建置結合的 .bsc 檔。  
  
## 請參閱  
 [C\/C\+\+ 建置工具](../../build/reference/c-cpp-build-tools.md)   
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)