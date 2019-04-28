---
title: LIBRARY
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: b43f269726e8925abeefd41aab0edfd57b071035
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291089"
---
# <a name="library"></a>LIBRARY

會告訴 LINK 以建立 DLL。 在此同時，連結會建立匯入程式庫，除非在組建中使用.exp 檔。

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>備註

*程式庫*引數會指定 DLL 的名稱。 您也可以使用[/out](out-output-file-name.md)連結器選項來指定 DLL 的輸出名稱。

基底 =*地址*引數設定作業系統使用載入的 DLL 的基底位址。 這個引數會覆寫預設的 DLL 位置 0x10000000。 請參閱的說明[基底/](base-base-address.md)基底位址的詳細資料的選項。

請務必使用[/DLL](dll-build-a-dll.md)建置 DLL 時，連結器選項。

## <a name="see-also"></a>另請參閱

[模組定義陳述式的規則](rules-for-module-definition-statements.md)
