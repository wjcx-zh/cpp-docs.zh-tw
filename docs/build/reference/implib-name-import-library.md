---
title: /IMPLIB (名稱匯入程式庫)
ms.date: 11/04/2016
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
ms.openlocfilehash: 8d3793b11e7bd0430c94d89f9d40ec3627c4eb20
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413351"
---
# <a name="implib-name-import-library"></a>/IMPLIB (名稱匯入程式庫)

> /IMPLIB:*filename*

## <a name="parameters"></a>參數

*filename*<br/>
匯入程式庫的使用者指定的名稱。 它會取代預設的名稱。

## <a name="remarks"></a>備註

/IMPLIB 選項會覆寫建置包含匯出的程式時，會建立連結的匯入程式庫的預設名稱。 預設名稱由主要輸出檔和擴充功能的基底名稱。 lib。 如果指定了一個或多個項目，程式會包含匯出：

- [__Declspec （dllexport)](../../cpp/dllexport-dllimport.md)原始程式碼中的關鍵字

- [匯出](../../build/reference/exports.md).def 檔案中的陳述式

- [/匯出](../../build/reference/export-exports-a-function.md)LINK 命令中的規格

若未建立匯入程式庫，連結就會忽略 /IMPLIB。 如果沒有指定匯出，連結就不會建立匯入程式庫。 如果組建使用的匯出檔案時，匯入程式庫已經存在，而且不會建立一個，也會假設連結。 如需匯入程式庫和匯出檔案的資訊，請參閱[LIB 參考](../../build/reference/lib-reference.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**匯入程式庫**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
