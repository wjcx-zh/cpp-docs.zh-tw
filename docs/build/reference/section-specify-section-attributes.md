---
title: "/SECTION (指定區段屬性) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SECTION 連結器選項"
  - "區段屬性"
  - "SECTION 連結器選項"
  - "-SECTION 連結器選項"
ms.assetid: 92b69d81-e421-462e-b46f-7d0dff9b9d16
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SECTION (指定區段屬性)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SECTION:name,[[!]{DEKPRSW}][,ALIGN=#]  
```  
  
## 備註  
 \/SECTION 選項會變更區段的屬性，覆寫在編譯區段 .obj 檔時所設定的屬性。  
  
 在可移植執行檔 \(PE\) 中的一個區段大略相當於新的可執行檔 \(NE\) 中的一個區段或資源。  區段中含有程式碼或資料。  與 Segment 不同之處在於，區段 \(Section\) 是沒有大小限制的連結記憶體區塊。  有些區段中含有程式直接宣告和使用的程式碼或資料，而另一些資料區段則是由連結器和程式庫管理員 \(lib.exe\) 為您建立的，並且含有對作業系統十分重要的資訊。  如需有關 NE 檔的詳細資訊，請參閱知識庫文件〈Executable\-File Header Format〉\(Q65122\)。  您可以在 MSDN 文件庫或是在 [http:\/\/search.support.microsoft.com](http://support.microsoft.com) 找到知識庫文件。  
  
 請指定一個冒號 \(:\) 和一個區段 *name*。  *name* 需區分大小寫。  
  
 請勿使用下列名稱，因為它們會與標準名稱衝突。  例如，.sdata 是使用於 RISC 平台：  
  
-   .arch  
  
-   .bss  
  
-   .data  
  
-   .edata  
  
-   .idata  
  
-   .pdata  
  
-   .rdata  
  
-   .reloc  
  
-   .rsrc  
  
-   .sbss  
  
-   .sdata  
  
-   .srdata  
  
-   .text  
  
-   .xdata  
  
 請對區段指定一或多個屬性。  下面所列的屬性字元不分大小寫。  您必須指定要區段擁有的所有屬性；省略屬性字元會導致該屬性位元被關閉。  如果您不指定 R、W 或 E，則現有的讀取、寫入或可執行狀態將會保持不變。  
  
 若要取消屬性，請在屬性字元前面加一個驚嘆號 \(\!\)。  這些屬性字元的意義如下。  
  
|字元|屬性|意義|  
|--------|--------|--------|  
|E|執行|這個區段可以執行|  
|R|讀取|允許資料讀取作業|  
|W|寫入|允許資料寫入作業|  
|S|Shared|與載入影像的所有處理序共用區段|  
|D|可捨棄|將區段標記為可捨棄|  
|K|可快取|將區段標記為不可快取|  
|P|可分頁|將區段標記為不可分頁|  
  
 K 和 P 相當特殊，因為對應到它們的區段旗標是以負面意義表達的。  如果您在 .text 區段上指定它們之中的某一個 \(\/SECTION:.text,K\)，對於您以 [\/HEADERS](../../build/reference/headers.md) 選項執行 [DUMPBIN](../../build/reference/dumpbin-options.md) 時的區段旗標不會產生任何影響；因為它已經隱含快取了。  若要移除這項預設，請指定 \/SECTION:.text,\!K，且 DUMPBIN 將會顯示區段的特性，包括 "Not Cached"。  
  
 在 PE 檔中未設定 E、R 或 W 的區段可能會無效。  
  
 ALIGN*\=\#* 可以讓您指定針對特定區段的對齊值。  如需詳細資訊，請參閱 [\/ALIGN](../../build/reference/align-section-alignment.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)