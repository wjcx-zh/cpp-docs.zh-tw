---
title: "-Gs （控制堆疊檢查呼叫） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /GS
dev_langs: C++
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4c957ff59976406609a88bfbfe3e1f51af44d6c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (控制堆疊檢查呼叫)
控制堆疊探查。  
  
## <a name="syntax"></a>語法  
  
```  
/Gs[size]  
```  
  
## <a name="arguments"></a>引數  
 `size`  
 (選擇性) 在起始堆疊探查之前，本機變數可佔用的位元組數目。 如果**/Gs**選項指定不含`size`引數，就如同指定**/Gs0**，  
  
## <a name="remarks"></a>備註  
 堆疊探查是編譯器插入到每個函式呼叫的程式碼序列。 起始時，堆疊探查會良性地進入記憶體，深入達到存放函式本機變數所需的空間量。  
  
 如果函式本機變數需要的堆疊空間多於 `size` 個位元組，便會起始堆疊探查。 根據預設，編譯器產生的程式碼會在函式需要超過一頁的堆疊空間時，起始堆疊探查。 這相當於編譯器選項的**/Gs4096** x86， [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]，和 ARM 平台。 這個值允許應用程式和 Windows 記憶體管理員動態地在執行階段增加認可給程式堆疊的記憶體數量。  
  
> [!NOTE]
>  預設值**/Gs4096**可讓 Windows 在執行階段正確地成長的應用程式的程式堆疊。 我們建議您不要變更預設值，除非您確實知道為何必須變更它。  
  
 有些程式—例如虛擬裝置驅動程式—不需要這項預設的堆疊成長機制。 在這種情況下，便不需要堆疊探查，您可以將 `size` 設成大於任何函式存放本機變數所需要的值，讓編譯器停止產生堆疊探查。 不允許空間之間**/Gs**和`size`。  
  
 **/ Gs0**啟動每個函式呼叫，需要存放裝置的本機變數的堆疊探查。 這對效能可能會產生負面影響。  
  
 您可以使用來開啟或關閉堆疊探查[check_stack](../../preprocessor/check-stack.md)。 **/Gs**和`check_stack`pragma 在標準 C 程式庫常式沒有效果; 它們會影響您編譯的函式。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)