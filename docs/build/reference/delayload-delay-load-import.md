---
title: /DELAYLOAD (延遲載入匯入)
ms.date: 11/04/2016
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
ms.openlocfilehash: e92b470b7b5e76b39371f333cbbda150e7f6e8c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273350"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (延遲載入匯入)

> **/DELAYLOAD:**_dllname_

## <a name="parameters"></a>參數

*dllname*<br/>
您想要延遲載入的 DLL 名稱。

## <a name="remarks"></a>備註

/DELAYLOAD 選項會使 `dllname` 指定的 DLL 只在程式第一次呼叫該 DLL 中的函式時載入。 如需詳細資訊，請參閱 <<c0> [ 延遲載入 Dll 的連結器支援](linker-support-for-delay-loaded-dlls.md)。 您可以視需要多次使用此選項，指定您所選擇數目的 DLL。 當您連結您的程式，必須使用 Delayimp.lib，或者實作自己的延遲載入 helper 函式。

[/延遲](delay-delay-load-import-settings.md)選項會指定繫結和載入每一個延遲載入 dll 的選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 在 **連結器**資料夾中，選取**輸入**屬性頁。

1. 修改**延遲載入 Dll**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
