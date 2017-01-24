---
title: "在 Visual Studio 中產生資訊清單 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資訊清單 [C++]"
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在 Visual Studio 中產生資訊清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在專案的 \[**屬性頁**\] 對話方塊中控制某特定專案之資訊清單檔的產生，  只需在 \[**組態屬性**\] 索引標籤上，依序按一下 \[**連結器**\]、\[**資訊清單檔**\]、\[**產生資訊清單**\]。  根據預設，新專案的專案屬性會設定為要產生資訊清單檔，  不過，您也可以利用專案的 \[**產生資訊清單**\] 屬性來停用專案資訊清單的產生。  當這個屬性是設為 \[**是**\] 時，就會產生該專案的資訊清單，  否則，當連結器在解析應用程式程式碼的相依性時，會忽略組件資訊，且不會產生資訊清單。  
  
 Visual Studio 中的建置系統可讓資訊清單內嵌到最終二進位應用程式檔案內，或是以外部檔案的形式產生。  這個行為是經由 \[**專案屬性**\] 對話方塊中的 \[**內嵌資訊清單**\] 選項來控制。  若要設定這個屬性，請開啟 \[**資訊清單工具**\] 節點，然後選取 \[**輸入和輸出**\]。  如果資訊清單不是內嵌式，就是以外部檔案的方式產生，並儲存在最終二進位檔所在的目錄中。  如果已內嵌此資訊清單，Visual Studio 會使用下列程序來內嵌最終資訊清單：  
  
1.  當原始程式碼編譯成目的檔之後，連結器會收集相依組件的資訊，  當連結最終程式庫時，連結器會產生一個中繼資訊清單，之後會用它來產生最終資訊清單。  
  
2.  完成中繼資訊清單與連結作業之後，就會執行資訊清單工具以合併最終資訊清單，並將它儲存為外部檔案。  
  
3.  接著，專案建置系統會偵測資訊清單工具所產生的資訊清單和已內嵌於二進位檔中的資訊清單，其所包含的資訊是否不同。  
  
4.  如果內嵌於二進位檔中的資訊清單與資訊清單工具所產生的資訊清單不同，或是此二進位檔不包含內嵌的資訊清單，則 Visual Studio 將會再次叫用連結器，將二進位檔內的外部資訊清單檔當做資源的形式內嵌。  
  
5.  如果內嵌於二進位檔中的資訊清單和資訊清單工具所產生的資訊清單相同，建置就會前進至下一個建置步驟。  
  
 資訊清單是內嵌於最終二進位檔中做為文字資源，您可以在 Visual Studio 中開啟最終二進位檔來檢視資訊清單。  若要確保資訊清單指向正確的程式庫，請遵循[了解 Visual C\+\+ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)中所述的步驟，或是遵循[疑難排解](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)一節中所述的建議事項。  
  
## 請參閱  
 [如何：在 C\/C\+\+ 應用程式中嵌入資訊清單](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [私用組件](_win32_private_assemblies)   
 [資訊清單工具](http://msdn.microsoft.com/library/aa375649)   
 [了解 C\/C\+\+ 程式的資訊清單產生過程](../build/understanding-manifest-generation-for-c-cpp-programs.md)