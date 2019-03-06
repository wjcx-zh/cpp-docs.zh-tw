---
title: /MANIFESTINPUT (指定資訊清單輸入)
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: f0b60b1f9ebff4547017fcfac586f00625311937
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418801"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (指定資訊清單輸入)

指定要包含在內嵌於影像中的資訊清單中的資訊清單輸入的檔。

## <a name="syntax"></a>語法

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>參數

*filename*<br/>
要在內嵌資訊清單中包含的資訊清單檔案。

## <a name="remarks"></a>備註

**/MANIFESTINPUT**選項會指定要用來建立可執行檔映像中的內嵌資訊清單輸入檔案的路徑。 如果您有多個資訊清單輸入檔，請使用此參數多次，每個輸入檔案的一次。 資訊清單輸入的檔案會合併以建立內嵌資訊清單。 這個選項需要 **/manifest： 內嵌**選項。

無法直接在 Visual Studio 中設定這個選項。 請改用**額外的資訊清單檔案**的專案，以指定要包含的其他資訊清單檔案的屬性。 如需詳細資訊，請參閱 <<c0> [ 輸入和輸出、 資訊清單工具、 組態屬性\<專案名稱 > 屬性頁對話方塊](../../ide/input-and-output-manifest-tool.md)。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
