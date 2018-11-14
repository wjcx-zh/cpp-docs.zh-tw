---
title: /DEFAULTLIB (指定預設程式庫)
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 59a4b48e412cee6b2a90608747aa6fb3e1b79ca7
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326382"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (指定預設程式庫)

指定預設程式庫，以搜尋，以解析外部參考。

## <a name="syntax"></a>語法

> **/DEFAULTLIB**:_文件庫_

### <a name="arguments"></a>引數

*程式庫*<br/>
解析外部參考時所要搜尋的程式庫的名稱。

## <a name="remarks"></a>備註

**/DEFAULTLIB**選項會將其中一個*程式庫*連結在解析參考時所搜尋的程式庫的清單。 使用指定的程式庫 **/DEFAULTLIB**搜尋之後明確地指定命令列上，以及名為.obj 檔中的預設程式庫之前的程式庫。

當使用不含引數， [/NODEFAULTLIB （忽略所有預設程式庫）](../../build/reference/nodefaultlib-ignore-libraries.md)選項會覆寫所有 **/DEFAULTLIB**:*文件庫*選項。 **/NODEFAULTLIB**:*程式庫*選項會覆寫 **/DEFAULTLIB**:*文件庫*時相同*文件庫*中指定名稱。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 在 **其他選項**，輸入 **/DEFAULTLIB**:*文件庫*搜尋每個程式庫的選項。 選擇**確定**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](../../build/reference/setting-linker-options.md)
- [連結器選項](../../build/reference/linker-options.md)
