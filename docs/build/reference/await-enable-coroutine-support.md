---
title: -await （啟用協同程式不支援） |Microsoft 文件
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /await
- -await
dev_langs:
- C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78a62195ca28be49ed8c00dacacce003281699f9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="await-enable-coroutine-support"></a>/await （啟用協同程式不支援）  
  
使用 **/await**編譯器選項，啟用協同程式的編譯器支援。  
  
## <a name="syntax"></a>語法  
  
> /await  
  
## <a name="remarks"></a>備註  
  
**/Await**編譯器選項可讓 c + + 協同程式和關鍵字的編譯器支援**co_await**， **co_yield**，和**co_return**. 根據預設，這個選項為關閉狀態。 支援 Visual Studio 中的協同程式的相關資訊，請參閱[Visual Studio 小組部落格](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/)。 如需協同程式的標準提案的詳細資訊，請參閱[N4628 工作草稿、 協同程式的 c + + 擴充功能的技術規格](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf)。  

**/Await**選項是從開始使用 Visual Studio 2015。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. 開啟您的專案**屬性頁** 對話方塊。   
  
2. 在下**組態屬性**，依序展開**C/c + +** 資料夾，然後選擇 **命令列**屬性頁。  
  
3. 輸入 **/await**編譯器選項在**其他選項**方塊。 選擇**確定**或**套用**以儲存變更。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
  
[編譯器選項](../../build/reference/compiler-options.md)   
[設定編譯器選項](../../build/reference/setting-compiler-options.md)