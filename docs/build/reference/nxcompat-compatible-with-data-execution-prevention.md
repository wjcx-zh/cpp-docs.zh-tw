---
title: "/NXCOMPAT （與資料執行防止相容） |Microsoft 文件"
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /NXCOMPAT
dev_langs:
- C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4669c24c3e15fc82f4ba81c83b8892ed18c24a5e
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (與資料執行防止相容)

表示可執行檔是與 Windows 資料執行防止功能相容。

## <a name="syntax"></a>語法

> **/NXCOMPAT**[**: NO**]

## <a name="remarks"></a>備註

根據預設， **/NXCOMPAT**上。

**/Nxcompat: no**可用來明確指定可執行檔做為與資料執行防止功能相容。

如需詳細資料執行防止 」 的詳細資訊，請參閱下列文章：

- [資料執行防止 (DEP) 功能的詳細的說明](http://go.microsoft.com/fwlink/p/?linkid=157771)

- [資料執行防止](http://go.microsoft.com/fwlink/p/?linkid=157770)

- [資料執行防止 (內嵌 Windows)](http://go.microsoft.com/fwlink/p/?linkid=157768)

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選擇**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項**方塊。 選擇**確定**或**套用**以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)  
[連結器選項](../../build/reference/linker-options.md)  
