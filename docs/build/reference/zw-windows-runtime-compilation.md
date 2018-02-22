---
title: "-ZW （Windows 執行階段編譯） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
dev_langs:
- C++
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbaa6d708cf882d3f396cc2a68159a520a017f8d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="zw-windows-runtime-compilation"></a>/ZW (Windows 執行階段編譯)
編譯原始程式碼，以支援[!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) 來建立通用 Windows 平台 (UWP) 應用程式。  
  
 當您使用**/ZW**進行編譯時，一定要指定**/EHsc**以及。  
  
## <a name="syntax"></a>語法  
  
```cpp  
/ZW /EHsc  
/ZW:nostdlib /EHsc  
```  
  
## <a name="arguments"></a>引數  
 nostdlib  
 表示 Platform.winmd、Windows.Foundation.winmd 和其他預設 Windows 中繼資料 (.winmd) 檔案未自動包含在編譯中。 相反地，您必須使用[/FU (命名強制 #using 檔案)](../../build/reference/fu-name-forced-hash-using-file.md)編譯器選項來明確指定 Windows 中繼資料檔案。  
  
## <a name="remarks"></a>備註  
 當您指定**/ZW**選項時，編譯器支援下列功能：  
  
-   必要的中繼資料檔案、 命名空間、 資料類型和應用程式需要 Windows 執行階段中執行的函式。  
  
-   Windows 執行階段物件的參考計數 」 和 「 自動捨棄物件參考計數歸零時自動。  
  
 因為 incremental 連結器不支援使用.obj 檔案中包含的 Windows 中繼資料**/ZW**選項， [/Gm （啟用最少重建）](../../build/reference/gm-enable-minimal-rebuild.md)選項與不相容**/ZW**.  
  
 如需詳細資訊，請參閱[Visual c + + 語言參考](../../cppcx/visual-c-language-reference-c-cx.md)。  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)