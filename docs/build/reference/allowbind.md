---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind_bind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4f5b662223914cbb4970188595afb52cc2500cd4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440385"
---
# <a name="allowbind"></a>/ALLOWBIND

指定 DLL 是否可以繫結。

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>備註

**/ALLOWBIND**選項會在 DLL 的標頭中設定一個位，指出允許系結影像的 .exe。 當載入器不需要重設基底，並針對每個參考的 DLL 執行位址修復時，系結可以讓影像更快載入。 如果 DLL 已進行數位簽署，您可能不想要系結，系結會使簽章無效。 如果使用支援 ASLR 的 Windows 版本上的 **/DYNAMICBASE** ，啟用映射的位址空間配置隨機載入（ASLR），系結就不會有任何作用。

使用 **/ALLOWBIND： NO**可防止 Bind 系結 DLL。

如需詳細資訊，請參閱[/ALLOWBIND](allowbind-prevent-dll-binding.md)連結器選項。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)
