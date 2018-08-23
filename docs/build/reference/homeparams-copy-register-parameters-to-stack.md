---
title: -homeparams （暫存器參數複製到堆疊） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /homeparams
dev_langs:
- C++
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfd6b8c77d972eb4606e7095bc5f733e7db16ea6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572253"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (將暫存器參數複製到堆疊)
在函式進入時，強制暫存器中所傳遞的參數寫入至堆疊上的位置。  
  
## <a name="syntax"></a>語法  
  
```  
/homeparams  
```  
  
## <a name="remarks"></a>備註  
 這個編譯器選項是僅適用於 x64 編譯器 （原生和跨編譯）。  
  
 當參數傳入 x64 編譯時，呼叫慣例需要參數需要，即使在暫存器中傳遞的參數。 如需詳細資訊，請參閱 <<c0> [ 參數傳遞](../../build/parameter-passing.md)。 不過，在發行組建的預設值，將暫存器參數將不會寫堆疊中，已針對參數提供的空間。 這可讓您難以偵錯最佳化 （發行） 組建您的程式。  
  
 用於發行組建，而 **/homeparams**以確保您可以偵錯您的應用程式。 **/homeparams**的確效能缺點，因為它需要載入到堆疊上的暫存器參數循環。  
  
 在偵錯組建中，一律會填入堆疊暫存器中傳遞的參數。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  在 [其他選項]  方塊中，輸入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)