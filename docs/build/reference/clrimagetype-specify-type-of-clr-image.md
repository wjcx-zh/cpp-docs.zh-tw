---
title: "-CLRIMAGETYPE （指定 CLR 映像類型） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs: C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7d8edd6c9e62456e54ac6228f25d7f923a6813c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (指定 CLR 映像類型)
```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## <a name="remarks"></a>備註  
 連結器接受原生物件，而且也 MSIL 物件都會使用編譯[/clr](../../build/reference/clr-common-language-runtime-compilation.md)，/clr: pure，或 /clr: safe。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。 在相同組建中傳遞混合物件時，所產生輸出檔案的可驗證性將預設為同等於輸入模組最低層級的可驗證性。 例如，如果同時將安全模組和純模組傳遞至連結器，輸出檔案將是純模組。 如果您將原生映像和混合的模式映像 (使用編譯的**/clr**)，產生的映像將會以混合的模式映像。  
  
 如果您有需要，您可使用 /CLRIMAGETYPE 來指定較低層級的可驗證性。  
  
 在 .NET 4.5，/CLRIMAGETYPE 支援 SAFE32BITPREFERRED 選項。 這會設定 (在映像的 PE 標頭中) 旗標表示 MSIL 物件為安全的，且可以執行於所有平台，不過最好執行於 32 位元執行環境。 這個選項可讓應用程式執行於 ARM 平台，並指定應用程式要執行於 64 位元作業系統的 WOW64 下，而不是使用 64 位元執行環境。  
  
 當使用已編譯的.exe **/clr**或**/clr: pure**執行 wow64，可讓一個在 64 位元作業系統上執行的 32 位元應用程式在 64 位元作業系統上執行應用程式。 根據預設，使用編譯的.exe **/clr: safe**作業系統的 64 位元支援下執行。 不過，很可能您安全的應用程式會載入 32 位元元件。 在此情況下，它會載入 32 位元應用程式時，將會失敗安全映像作業系統的 64 位元支援下執行。 在 64 位元作業系統上載入 32 位元元件時，若要確保安全映像能繼續執行，請使用 /CLRIMAGETYPE:SAFE32BITPREFERRED 選項。 如果您的程式碼不需要在 ARM 平台執行，您可以指定 /CLRIMAGETYPE:PURE 選項變更中繼資料 (.corflags)，標記其將執行於 WOW64 (並替代為您的進入點符號)：  
  
 **cl /clr:safe t.cpp /link /clrimagetype:pure /entry:?main@@$$HYMHXZ /subsystem:console**  
  
 如需如何判斷檔案之 CLR 映像類型的資訊，請參閱 [/CLRHEADER](../../build/reference/clrheader.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**進階**屬性頁。  
  
5.  修改**CLR 映像類型**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)