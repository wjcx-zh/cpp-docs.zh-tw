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
ms.openlocfilehash: 13987b4ba9c25db0f5417da562ff86f4230937d7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808296"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

指定是否要產生可執行映像可以隨機重定基底在載入時所使用的第一次在 Windows Vista 中可用的 Windows 位址空間配置隨機載入 (ASLR) 功能。

## <a name="syntax"></a>語法

> **/DYNAMICBASE**[**:NO**]

## <a name="remarks"></a>備註

**/DYNAMICBASE**選項會修改的標頭*可執行映像*，.dll 或.exe 檔案，以指出是否應該隨機重定基底在載入期間，應用程式，並可讓虛擬位址配置隨機載入，這會影響之虛擬記憶體位置的堆積，堆疊和其他作業系統配置。 **/DYNAMICBASE**選項適用於 32 位元和 64 位元的映像。 Windows Vista 和更新版本的作業系統上可支援 ASLR。 選項會忽略先前的作業系統。

根據預設， **/DYNAMICBASE**已啟用。 若要停用此選項，請使用 **/dynamicbase: no**。 **/DYNAMICBASE**選項是為了[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)選項影響。

## <a name="see-also"></a>另請參閱

- [EDITBIN 選項](editbin-options.md)
- [Windows ISV 軟體安全性防禦措施](https://msdn.microsoft.com/library/bb430720.aspx)