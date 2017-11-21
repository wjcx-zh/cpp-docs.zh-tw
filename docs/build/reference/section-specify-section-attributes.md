---
title: "-區段 （指定區段屬性） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /section
dev_langs: C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.assetid: 92b69d81-e421-462e-b46f-7d0dff9b9d16
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e3fd7e844d77b9a92408c0708542a4f8f5edf304
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="section-specify-section-attributes"></a>/SECTION (指定區段屬性)
```  
/SECTION:name,[[!]{DEKPRSW}][,ALIGN=#]  
```  
  
## <a name="remarks"></a>備註  
 /SECTION 選項會變更區段中，覆寫在編譯區段.obj 檔時，設定屬性的屬性。  
  
 可攜式執行檔 (PE) 中的區段等於大約為區段或新的可執行檔 (NE) 檔案中的資源。 各節包含程式碼或資料。 不同於區段，區段會是沒有大小限制的連續記憶體區塊。 某些章節包含程式碼或程式直接宣告和使用，而其他資料區段會為您建立由連結器和程式庫管理員 (lib.exe)，並包含作業系統内容的資訊的資料。 如需有關新檔案的詳細資訊，請參閱知識庫文章 「 可執行檔標頭格式 」 (Q65122)。 您可以在 MSDN Library，或找到知識庫文章[http://support.microsoft.com](http://support.microsoft.com)。  
  
 指定冒號 （:） 和區段*名稱*。 *名稱*區分大小寫。  
  
 請勿下列名稱，因為它們會與標準名稱發生衝突。 例如，.sdata RISC 平台上使用：  
  
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
  
 指定一或多個區段的屬性。 下面列出的屬性字元不區分大小寫。 您必須指定您想要有; 區段的所有屬性省略的屬性字元會關閉該屬性位元。 如果您未指定 R、 W、 或 E，現有的讀取、 寫入或可執行檔的狀態維持不變。  
  
 要變換正負號的屬性，在之前它一個內含驚嘆號 （！） 的字元。 如下所示的屬性字元意義。  
  
|字元|屬性|意義|  
|---------------|---------------|-------------|  
|E|執行|區段，則可執行檔|  
|R|讀取|允許對於資料的讀取的作業|  
|W|Write|允許對於資料的寫入作業|  
|S|Shared|共用區段載入影像的所有處理程序|  
|D|可捨棄|標記為可捨棄區段|  
|K|快取|標記為不可快取區段|  
|P|分頁|標記為不可分頁區段|  
  
 K 和 P 相當罕見，負的意義上是對應到它們的區段旗標。 如果您指定其中一個在.text 區段 (/ 區段：.text、 K)，會有任何差異 > 一節旗標執行時[DUMPBIN](../../build/reference/dumpbin-options.md)與[/HEADERS](../../build/reference/headers.md)選項; 已隱含已快取。 若要移除預設值，指定 /SECTION:.text ！K 和 DUMPBIN 會顯示一節的特性，包括 「 無法快取 」。  
  
 沒有 E、 R、 設定或 W PE 檔中的區段可能會無效。  
  
 對齊*=#* 可讓您指定的特定區段的對齊值。 請參閱[/對齊](../../build/reference/align-section-alignment.md)如需詳細資訊。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)