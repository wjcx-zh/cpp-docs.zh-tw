---
title: C++標準程式庫標頭檔
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: dc337ef078108d86849aa7b7452512dfb69e6e18
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341120"
---
# <a name="c-standard-library-header-files"></a>C++標準程式庫標頭檔

C++標準程式庫和延伸模組的標頭檔 (依類別)。

## <a name="headers-by-category"></a>依類別的標頭

::: moniker range=">=vs-2017"

| 分類 | 頁首 |
| - | - |
| [演算法](../cpp/algorithms-modern-cpp.md) | 演算法 > [、 b>\< ](cstdlib.md)、 [數值\<>](numeric.md) [ \< ](algorithm.md) |
| 不可部分完成的作業 |  不可部分完成 ><sup>11</sup> [ \< ](atomic.md) |
| C 程式庫包裝函式 | [ \< ](cfenv.md) <sup></sup> [ \< ](cerrno.md) [ \<cassert >](cctype.md)、 [x > 11 a b、cctype >、cerrno> >、cfenv > 11、 \< ](ccomplex.md) [ \< ](cassert.md) <sup></sup> [ \<t >](cfloat.md)、<sup> </sup> [ \<cinttypes >](cinttypes.md)11、 [ \<ciso646 >](ciso646.md)<sup>b</sup>、 [ \<climits >](climits.md)、 [ \<clocale >](clocale.md)、 [ h\<>](cmath.md)、 [ csetjmp>、csignal>、cstdalign>11ab、cstdarg>、\< ](csetjmp.md) [ \< ](cstdarg.md) [ \< ](csignal.md) [ \< ](cstdalign.md) <sup></sup> [ \<cstdbool >](cstdbool.md)<sup>11 a b</sup>、 [ \<cstddef >](cstddef.md)、 [ \<cstdint >](cstdint.md)<sup>11</sup>、 [ \<cstdio> >](cstdio.md)、 [ \<b >](cstdlib.md)、 [ cstring\<>](cstring.md)、<sup> </sup> [ \< ](ctime.md) <sup></sup> [ \< ](cuchar.md) [ \< ](cwchar.md) [ ctgmath>11\< ](ctgmath.md)a b、ctime >、cuchar > 11、cwchar >、 [ cwctype\<>](cwctype.md) |
| 概念 | \<><sup>20</sup>的概念 |
| [容器](../cpp/containers-modern-cpp.md) | |
| 序列容器 | <sup></sup> <sup></sup> [陣列\<>](array.md)11, [ deque>,forward_list>11,清單>,向量>\< ](deque.md) [ \< ](forward-list.md) [ \< ](list.md) [ \< ](vector.md) |
| 已排序的關聯容器| [\<map>](map.md)、[\<set>](set.md) |
| 未排序的關聯容器 | unordered_map ><sup>11</sup>, [ unordered_set>\< ](unordered-set.md) <sup>11</sup> [ \< ](unordered-map.md) |
| 容器配接器 | [\<queue>](queue.md)、[\<stack>](stack.md) |
| 容器視圖 | \<span ><sup>20</sup> |
| [錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md) | <sup></sup> [ cassert\<>](cassert.md) [、 exception\<>](exception.md) [、 stdexcept>\<>](stdexcept.md) [、 system_error\<>](system-error.md)11 |
| 一般公用程式 | \<任何 ><sup>17</sup>、 [ \<bitset >](bitset.md)、 \<charconv ><sup>17</sup>、 [ \<b >](cstdlib.md)、 \<執行 ><sup>17</sup>、 [ \<功能 >](functional.md)、 [記憶體\<>](memory.md), \< [ \< ](ratio.md) <sup> </sup> <sup> </sup> <sup> </sup>memory_resource > 17, 選擇性 > 17, 比率 > 11, scoped_allocator > \< [ \<](scoped-allocator.md) <sup>11</sup>,<sup> </sup> <sup> </sup> <sup> </sup> [ \< ](type-traits.md) [ \< ](typeindex.md) [ \< ](utility.md) [元\<組 >](tuple.md)11, type_traits > 11, typeindex > 11, 公用程式 >,\<variant ><sup>17</sup> |
| [I/o 和格式設定](../cpp/string-and-i-o-formatting-modern-cpp.md) | <sup></sup> <sup></sup> [ cinttypes\<>](cinttypes.md)11、 [ cstdio>>、filesystem>17、am>、p>、\< ](cstdio.md) [ \< ](filesystem.md) [ \< ](fstream.md) [ \< ](iomanip.md) [ ios\<>](ios.md)、 [ iosfwd>、iostream>、istream>、ostream>、sstream>\< ](iosfwd.md) [ \< ](iostream.md) [ \< ](istream.md) [ \< ](ostream.md) [ \< ](sstream.md)\< [ 、\<streambuf >](streambuf.md) [ 、\<strstream >](strstream.md)<sup>c</sup>、syncstream ><sup>20</sup> |
| 迭代器 | [\<iterator>](iterator.md) |
| 語言支援 | \< \< \< <sup></sup> <sup></sup> <sup></sup> [ t\<>](cfloat.md) [、 climits\<>](climits.md) [、 codecvt\<>](codecvt.md)11 a、比較 > 20、合約 > 20、協同程式 ><sup>20</sup>、 [ \<csetjmp >](csetjmp.md)、 [ \<csignal >](csignal.md)、 [ \<cstdarg >](cstdarg.md)、 [ \<cstddef >](cstddef.md)、 [ \<cstdint >](cstdint.md) <sup>11</sup> <sup> </sup> [, b\<>](cstdlib.md) [,例外\<](exception.md)狀況 > [ ,\<initializer_list >](initializer-list.md)11 [ ,\<限制 >](limits.md) [ ,\<新 >](new.md), [ \<typeinfo >](typeinfo.md), \<版本 ><sup>20</sup> |
| 當地語系化 | [ \< ](locale.md) <sup></sup> [ clocale>\< ](cvt-wbuffer.md)、 [codecvt > 11 a、cvt/wbuffer >、cvt/wstring >、locale > \< ](codecvt.md) [ \< ](cvt-wstring.md) [ \< ](clocale.md) |
| 數學和數值 | \<bit ><sup>20</sup>、 [ \<cfenv >](cfenv.md)<sup>11</sup>、 [ \<h >](cmath.md)、 [ \<複雜 >](complex.md)、 [ \<b >](cstdlib.md)、 [ \<限制 >](limits.md)、 [ 數值\<>](numeric.md),<sup> </sup> <sup> </sup> [隨機\<>](random.md)11 [,比率>11,valarray>\< ](ratio.md) [ \< ](valarray.md) |
| [記憶體管理](../cpp/smart-pointers-modern-cpp.md) | <sup></sup> <sup></sup> [配置器>\< ](new.md)、 \< [ \< ](scoped-allocator.md) [ memory\<>](memory.md)、memory_resource > 17、new >、scoped_allocator > 11 [ \< ](allocators-header.md) |
| 多執行緒 | <sup></sup> <sup></sup> <sup></sup> <sup></sup> [ \< ](condition-variable.md) [ \< ](future.md) [ \<不可部分](mutex.md)完成 > 11, condition_variable > 11, 未來 > 11, mutex > 11, [ \< ](atomic.md) [ \<shared_mutex >](shared-mutex.md)<sup>14</sup>, [ \<thread >](thread.md)<sup>11</sup> |
| 範圍 | \<範圍 ><sup>20</sup> |
| 規則運算式 | RegEx ><sup>11</sup> [ \< ](regex.md) |
| 字串和字元資料 | <sup></sup> [ cctype\<>](cctype.md)、 [ b>、cstring>、cuchar>11、cwchar>、cwctype\< ](cstdlib.md) [ \< ](cstring.md) [ \< ](cuchar.md) [ \< ](cwchar.md) [ \<>](cwctype.md) [ ,\<RegEx >](regex.md)<sup>11</sup>, [ \<string >](string.md), [ \<string_view >](string-view.md)<sup>17</sup> |
| 時間 | chrono ><sup>11</sup>, [ ctime\<>](ctime.md) [ \< ](chrono.md) |

<sup>11</sup>新增 c + + 11 標準。
c + + 14 standard 中加入了<sup>14</sup>個。
<sup>17</sup>加上 c + + 17 標準。
<sup>20</sup>在 Draft c + + 20 standard 中加入了20。
c + + 17 標準中<sup>的</sup>已被取代。
<sup>b</sup>已于 Draft c + + 20 standard 中移除。
<sup>c</sup> c + + 98 標準中已淘汰。

::: moniker-end

::: moniker range="vs-2015"

|分類|頁首|
|-|-|
|[演算法](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|C 程式庫包裝函式|[\<cassert>](cassert.md)、[\<cctype>](cctype.md)、[\<cerrno>](cerrno.md)、[\<cfenv>](cfenv.md)、[\<cfloat>](cfloat.md)、[\<cinttypes>](cinttypes.md)、[\<ciso646>](ciso646.md)、[\<climits>](climits.md)、[\<clocale>](clocale.md)、[\<cmath>](cmath.md)、[\<csetjmp>](csetjmp.md)、[\<csignal>](csignal.md)、[\<cstdarg>](cstdarg.md)、[\<cstdbool>](cstdbool.md)、[\<cstddef>](cstddef.md)、[\<cstdint>](cstdint.md)、[\<cstdio>](cstdio.md)、[\<cstdlib>](cstdlib.md)、[\<cstring>](cstring.md)、[\<ctgmath>](ctgmath.md)、[\<ctime>](ctime.md)、[\<cwchar>](cwchar.md)、[\<cwctype>](cwctype.md)|
|[容器](../cpp/containers-modern-cpp.md)||
|序列容器|[陣列\<>](array.md)、 [ deque>、forward_list>、list>、vector>\< ](deque.md) [ \< ](forward-list.md) [ \< ](list.md) [ \< ](vector.md)|
|已排序的關聯容器| [\<map>](map.md)、[\<set>](set.md)|
|未排序的關聯容器|unordered_map >、 [ \< ](unordered-map.md) [ unordered_set>\<](unordered-set.md)|
|介面卡容器|[\<queue>](queue.md)、[\<stack>](stack.md)|
|[錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md)|例外狀況 >、 [ \<stdexcept> >](stdexcept.md)、 [ \<system_error >](system-error.md) [ \< ](exception.md)|
|[I/o 和格式設定](../cpp/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md)、[\<fstream>](fstream.md)、[\<iomanip>](iomanip.md)、[\<ios>](ios.md)、[\<iosfwd>](iosfwd.md)、[\<iostream>](iostream.md)、[\<istream>](istream.md)、[\<ostream>](ostream.md)、[\<sstream>](sstream.md)、[\<streambuf>](streambuf.md)、[\<strstream>](strstream.md)|
|迭代器|[\<iterator>](iterator.md)|
|當地語系化|[\<codecvt>](codecvt.md)、[\<cvt/wbuffer>](cvt-wbuffer.md)、[\<cvt/wstring>](cvt-wstring.md)、[\<locale>](locale.md)|
|數學和數值|[\<complex>](complex.md)、[\<limits>](limits.md)、[\<numeric>](numeric.md)、[\<random>](random.md)、[\<ratio>](ratio.md)、[\<valarray>](valarray.md)|
|[記憶體管理](../cpp/smart-pointers-modern-cpp.md)|配置器 > [、記憶體\<>](memory.md)、 [新\<>](new.md)、 [ scoped_allocator\<>](scoped-allocator.md) [ \< ](allocators-header.md)|
|多執行緒|[ \< ](future.md) [ \< ](condition-variable.md) [不可部分\<](mutex.md)完成的 >, condition_variable >, 未來的 >, mutex >, [ \<shared_mutex >](shared-mutex.md), 執行緒[ \< ](atomic.md) [ \<>](thread.md)|
|其他公用程式|[ bitset\<>](bitset.md)、 [ chrono>、功能>、initializer_list>、元組>、type_traits\< ](chrono.md) [ \< ](functional.md) [ \< ](initializer-list.md) [ \< ](tuple.md) [ \<>](type-traits.md) [ ,\<typeinfo >](typeinfo.md), [ \<typeindex >](typeindex.md), [ \<公用程式 >](utility.md)|
|字串和字元資料|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用C++程式庫標頭](using-cpp-library-headers.md)\
[C++標準程式庫](cpp-standard-library-reference.md)
