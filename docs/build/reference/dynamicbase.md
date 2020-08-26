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
ms.openlocfilehash: 5451e3d16883eef225aebc3c420e6c0700947ad6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842577"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

指定是否產生可執行檔映射，該映射可在載入時隨機重定基底，方法是使用 windows Vista 中第一次可用 Windows 的位址空間配置隨機載入 (ASLR) 功能。

## <a name="syntax"></a>語法

> **/DYNAMICBASE**[**： NO**]

## <a name="remarks"></a>備註

**/DYNAMICBASE**選項會修改*可執行檔映射*（.dll 或 .exe 檔案）的標頭，以指出應用程式是否應該在載入時隨機重定基底，並啟用虛擬位址配置隨機載入，這會影響堆積、堆疊和其他作業系統配置的虛擬記憶體位置。 **/DYNAMICBASE**選項同時適用于32位和64位的映射。 Windows Vista 和更新版本的作業系統支援 ASLR。 舊版作業系統會忽略此選項。

預設會啟用 **/DYNAMICBASE** 。 若要停用此選項，請使用 **/DYNAMICBASE： NO**。 需要有 **/DYNAMICBASE** 選項， [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) 選項才會有效果。

## <a name="see-also"></a>另請參閱

- [EDITBIN 選項](editbin-options.md)
- [Windows ISV 軟體安全性防禦措施](/previous-versions/bb430720(v=msdn.10))
