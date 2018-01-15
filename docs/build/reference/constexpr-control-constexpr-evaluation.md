---
title: "constexpr （控制項 constexpr 評估版） |Microsoft 文件"
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /constexpr
- -constexpr
dev_langs: C++
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e594eb697c8972d28b513a3638d3eb704258b5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr （控制項 constexpr 評估版）  
  
使用**/constexpr**編譯器選項，以控制參數`constexpr`在編譯時期評估。  
  
## <a name="syntax"></a>語法  
  
> /constexpr:depth*N*  
> /constexpr:backtrace*N*  
> /constexpr:*N*  
  
## <a name="arguments"></a>引數  
  
**深度***N*  
限制的遞迴深度`constexpr`函式引動過程*N*層級。 預設值為 512。  
  
**反向追蹤***N*  
最多顯示*N* `constexpr`診斷中的評估作業。 預設值為 10。  
  
**步驟***N*  
終止`constexpr`之後評估*N*步驟。 預設值為 100,000。  
  
## <a name="remarks"></a>備註  
  
**/Constexpr**編譯器選項可控制的編譯時期評估`constexpr`運算式。 若要防止編譯器花費太多時間在控制評估步驟、 遞迴層級，以及反向追蹤深度`constexpr`評估。 如需有關`constexpr`語言項目，請參閱[constexpr （c + +）](../../cpp/constexpr-cpp.md)。  

**/Constexpr**選項會從開始使用 Visual Studio 2015。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. 開啟您的專案**屬性頁** 對話方塊。   
  
2. 在下**組態屬性**，依序展開**C/c + +**資料夾，然後選擇 **命令列**屬性頁。  
  
3. 輸入任何**/constexpr**編譯器選項，在**其他選項**方塊。 選擇**確定**或**套用**以儲存變更。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
  
[編譯器選項](../../build/reference/compiler-options.md)   
[設定編譯器選項](../../build/reference/setting-compiler-options.md)