---
title: /MANIFESTINPUT (指定資訊清單輸入)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 7b7bd54f98003d9158276fcf75fd61ffb5348585
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606470"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (指定資訊清單輸入)

指定資訊清單輸入檔, 以包含在影像內嵌的資訊清單中。

## <a name="syntax"></a>語法

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>參數

*filename*<br/>
要包含在內嵌資訊清單中的資訊清單檔。

## <a name="remarks"></a>備註

**/MANIFESTINPUT**選項會指定要用來在可執行映射中建立內嵌資訊清單的輸入檔路徑。 如果您有多個資訊清單輸入檔, 請多次使用參數, 針對每個輸入檔執行一次。 資訊清單輸入檔會進行合併, 以建立內嵌的資訊清單。 此選項需要 **/MANIFEST: EMBED**選項。

此選項不能直接在 Visual Studio 中設定。 相反地, 請使用專案的 [**其他資訊清單**檔] 屬性來指定要包含的其他資訊清單檔。 如需詳細資訊, 請參閱[資訊清單工具屬性頁](manifest-tool-property-pages.md)。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
