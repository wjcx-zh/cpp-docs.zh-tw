---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: 54644d9df546299be3b688f9745a121592938df6
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373615"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

指定是否要產生可執行映射，以在載入時使用 windows Vista 中第一次提供的 Windows 的位址空間配置隨機載入（ASLR）功能來隨機重定基底。

## <a name="syntax"></a>語法

> **/DYNAMICBASE**[**： NO**]

## <a name="remarks"></a>備註

**/DYNAMICBASE**選項會修改*可執行映射*（.dll 或 .exe 檔案）的標頭，以指出是否應在載入時隨機重定基底應用程式，並啟用虛擬位址配置隨機，這會影響堆積、堆疊和其他作業系統配置的虛擬記憶體位置。 **/DYNAMICBASE**選項同時適用于32位和64位的映射。 Windows Vista 和更新版本的作業系統都支援 ASLR。 舊版作業系統會忽略此選項。

根據預設，會啟用 **/DYNAMICBASE** 。 若要停用此選項，請使用 **/DYNAMICBASE： NO**。 必須要有 **/DYNAMICBASE**選項， [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)選項才會生效。

## <a name="see-also"></a>另請參閱

- [EDITBIN 選項](editbin-options.md)
- [Windows ISV 軟體安全性防禦](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
