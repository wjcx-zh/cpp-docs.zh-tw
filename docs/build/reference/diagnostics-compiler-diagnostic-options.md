---
title: "為診斷 （編譯器診斷選項） |Microsoft 文件"
ms.custom: 
ms.date: 11/11/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs: C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4034e875c2feb52f938edeb4b05383d954476a21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/diagnostics （編譯器診斷選項）  
  
使用**/diagnostics**編譯器選項，來指定要顯示的錯誤和警告的位置資訊。  
  
## <a name="syntax"></a>語法  
  
```  
/diagnostics:{caret|classic|column}
```  

## <a name="remarks"></a>備註  
**/Diagnostics**編譯器選項可控制顯示的錯誤與警告資訊。  
  
**/Diagnostics:classic**選項是預設值，它會報告只找到問題所在的行號。  
  
**/Diagnostics:column**選項也會包含找到問題的資料行。 這可協助您找出特定的語言建構或造成問題的字元。  
  
**/Diagnostics:caret**選項會包含資料行的位置找不到的問題，以及下已偵測到問題的位置中的一行程式碼會將插入號 (^)。  
  
請注意，在某些情況下，編譯器不會偵測的問題發生的位置。 例如，直到其他、 未預期的符號已發生，可能無法偵測遺漏的分號。 報告資料行，並且插入號會放置於其中編譯器偵測到的項目則是錯誤，這不一定是在您要讓您的更正。  
  
**/Diagnostics**選項才可以使用 Visual Studio 2017 中啟動。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. 開啟您的專案**屬性頁** 對話方塊。   
  
2. 在下**組態屬性**，依序展開**C/c + +**資料夾，然後選擇 **一般**屬性頁。  
  
3. 使用中的下拉式清單控制項**診斷格式**欄位來選取診斷顯示選項。 選擇**確定**或**套用**以儲存變更。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)