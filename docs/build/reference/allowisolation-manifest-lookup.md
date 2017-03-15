---
title: "/ALLOWISOLATION (資訊清單查閱) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ALLOWISOLATION"
  - "VC.Project.VCLinkerTool.AllowIsolation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWISOLATION 連結器選項"
  - "-ALLOWISOLATION 連結器選項"
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /ALLOWISOLATION (資訊清單查閱)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定資訊清單查閱的行為。  
  
## 語法  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## 備註  
 **\/ALLOWISOLATION:NO** 指出已載入 DLL，好像沒有資訊清單一樣，並導致連結器在選擇項標頭的 `DllCharacteristics` 欄位中，設定 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 位元。  
  
 **\/ALLOWISOLATION** 造成作業系統執行資訊清單查閱並載入。  
  
 **\/ALLOWISOLATION** 為預設值。  
  
 可執行檔停用隔離時，Windows 載入器並不會試圖尋找最新建立處理序的應用程式資訊清單。  即使可執行檔中有資訊清單，或是資訊清單以 *executable\-name***.exe.manifest** 的名稱放置於與可執行檔相同的目錄中，新處理序也不會有預設啟動內容。  
  
 如需詳細資訊，請參閱[資訊清單檔參考](http://msdn.microsoft.com/library/aa375632)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**資訊清單檔案**\] 屬性頁。  
  
5.  修改 \[**允許隔離**\] 屬性。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)