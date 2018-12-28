---
title: /homeparams (將暫存器參數複製到堆疊)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: ffb5ca602feb7a369bb31d0277834786d66ac12a
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627431"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (將暫存器參數複製到堆疊)

也會寫入至其位置函式進入時，堆疊上的暫存器中傳遞的強制參數。

## <a name="syntax"></a>語法

> **/homeparams**

## <a name="remarks"></a>備註

這個編譯器選項僅適用於原生和跨編譯器的 x64 為目標。

X64 呼叫慣例需要堆疊空間配置給所有參數，即使在暫存器中傳遞的參數。 如需詳細資訊，請參閱 <<c0> [ 參數傳遞](../../build/x64-calling-convention.md#parameter-passing)。 根據預設，暫存器參數不會複製到配置給其發行組建中的堆疊空間。 這可讓您難以偵錯您的程式最佳化的發行組建。

您可以使用發行組建 **/homeparams**選項來強制編譯器將複製暫存器參數複製到堆疊，以確保您可以偵錯您的應用程式。 **/homeparams**的確效能缺點，因為它需要額外的週期，以載入至堆疊暫存器參數。

在偵錯組建，一律會填入堆疊暫存器中傳遞的參數。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 開啟**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 輸入中的編譯器選項**其他選項** 方塊中。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)