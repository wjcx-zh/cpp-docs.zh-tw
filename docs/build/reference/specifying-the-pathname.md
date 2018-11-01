---
title: 指定路徑名稱
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: f83adcb87994d13edd1c1579183377a365e2051e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638356"
---
# <a name="specifying-the-pathname"></a>指定路徑名稱

每個輸出檔案 選項會接受*pathname*引數，可以指定的位置和輸出檔案的名稱。 引數可以包含磁碟機名稱、 目錄和檔案名稱。 不允許有空格的選項與引數之間。

如果*pathname*包含檔案名稱不含副檔名，編譯器會產生輸出的預設延伸模組。 如果*pathname*包含一個目錄，但沒有檔案名稱，編譯器會使用指定的目錄中的預設名稱建立檔案。 預設名稱根據原始程式檔和輸出檔的類型為基礎的預設延伸模組的基底名稱。 如果您省略*pathname*完全，編譯器會建立檔案的預設目錄的預設名稱。

或者， *pathname*引數可以是裝置名稱 （AUX、 CON、 PRN、 或 NUL），而不是檔案名稱。 請勿使用選項和裝置名稱或冒號之間有空白的裝置名稱的一部分。

|裝置名稱|表示|
|-----------------|----------------|
|AUX|輔助裝置|
|CON|主控台|
|PRN|印表機|
|NUL|空的裝置 （沒有建立的檔案）|

## <a name="example"></a>範例

下列命令列會傳送到印表機的對應檔：

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>另請參閱

[輸出檔 (/F) 選項](../../build/reference/output-file-f-options.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)