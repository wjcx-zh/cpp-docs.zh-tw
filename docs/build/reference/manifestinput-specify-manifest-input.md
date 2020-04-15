---
title: /MANIFESTINPUT (指定資訊清單輸入)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: d7c8351c915f5666ada9939df686c81c86ab89ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337497"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (指定資訊清單輸入)

指定要包含在影像中的清單中的清單輸入檔。

## <a name="syntax"></a>語法

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>參數

*檔案名稱*<br/>
要包含在嵌入清單中的清單檔。

## <a name="remarks"></a>備註

**/MANIFESTINPUT**選項指定用於在可執行映射中創建嵌入清單的輸入文件的路徑。 如果您有多個清單輸入檔,請使用該開關多次— 每個輸入檔一次。 合併清單輸入檔以建立嵌入的清單。 此選項需要 **/MANIFEST:EMBED**選項。

無法直接在可視化工作室中設置此選項。 相反,請使用專案**的其他清單檔**屬性指定要包括的其他清單檔。 有關詳細資訊,請參閱[清單工具屬性頁](manifest-tool-property-pages.md)。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
