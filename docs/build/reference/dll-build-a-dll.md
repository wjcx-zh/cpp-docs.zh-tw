---
title: /DLL (建置 DLL)
ms.date: 11/04/2016
f1_keywords:
- /dll
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
ms.openlocfilehash: 71696e4ffae91ed1fa8a13e69e75523ce66e8361
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546329"
---
# <a name="dll-build-a-dll"></a>/DLL (建置 DLL)

```
/DLL
```

## <a name="remarks"></a>備註

/DLL 選項建置 DLL 做為主要輸出檔。 DLL 通常會包含可供其他程式的匯出。 有三種方法來指定匯出，建議使用的順序中所列：

1. [__declspec （dllexport)](../../cpp/dllexport-dllimport.md)原始程式碼中

1. [匯出](../../build/reference/exports.md).def 檔案中的陳述式

1. [/匯出](../../build/reference/export-exports-a-function.md)LINK 命令中的規格

程式可以使用一個以上的方法。

若要建置 DLL 的另一個方法是使用**程式庫**模組定義陳述式。 /BASE 和 /DLL 選項一起相當於**程式庫**陳述式。

未指定此選項，在開發環境;此選項僅供只能在命令列上的使用。 當您建立 DLL 專案與應用程式精靈 時，會設定這個選項。

請注意，是否您建立您匯入程式庫中第一步，建立.dll 之前，您必須傳遞同一組物件檔案建置.dll 時為您成功建置匯入程式庫時。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **組態屬性**資料夾。

1. 按一下 **一般**屬性頁。

1. 修改**組態類型**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)