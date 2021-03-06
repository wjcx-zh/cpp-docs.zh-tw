---
title: C + + 標準程式庫標頭檔
description: C + + 標準程式庫標頭檔，分類
ms.date: 08/31/2020
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: dfadfb99e10fdb916b3fb4dc515f89e6f9252fde
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352878"
---
# <a name="c-standard-library-header-files"></a>C + + 標準程式庫標頭檔

C + + 標準程式庫和擴充功能的標頭檔（依類別）。

## <a name="headers-by-category"></a>依類別區分的標頭

::: moniker range=">=vs-2017"

| 類別 | 標題 |
| - | - |
| [演算法](./algorithms.md) | [\<algorithm>](algorithm.md), [\<cstdlib>](cstdlib.md), [\<numeric>](numeric.md) |
| 不可部分完成的作業 |  [\<atomic>](atomic.md)<sup>rj-11</sup> |
| C 程式庫包裝函式 | [\<cassert>](cassert.md)、 [\<ccomplex>](ccomplex.md) <sup>11 a b</sup>、 [\<cctype>](cctype.md) 、 [\<cerrno>](cerrno.md) 、 [\<cfenv>](cfenv.md) <sup>11</sup>、 [\<cfloat>](cfloat.md) 、 [\<cinttypes>](cinttypes.md) <sup>11</sup>、 [\<ciso646>](ciso646.md) <sup>b</sup>、、、、、 [\<climits>](climits.md) [\<clocale>](clocale.md) [\<cmath>](cmath.md) [\<csetjmp>](csetjmp.md) [\<csignal>](csignal.md) [\<cstdalign>](cstdalign.md) <sup>11 a b</sup>、 [\<cstdarg>](cstdarg.md) 、 [\<cstdbool>](cstdbool.md) <sup>11 a</sup>b、 [\<cstddef>](cstddef.md) 、 [\<cstdint>](cstdint.md) <sup>11</sup>、 [\<cstdio>](cstdio.md) 、、、 [\<cstdlib>](cstdlib.md) [\<cstring>](cstring.md) [\<ctgmath>](ctgmath.md) <sup>11 a b</sup>、 [\<ctime>](ctime.md) 、 [\<cuchar>](cuchar.md) <sup>11</sup> [\<cwchar>](cwchar.md) 11、、[\<cwctype>](cwctype.md) |
| 概念 | \<concepts><sup>名</sup> |
| [容器](./stl-containers.md) | |
| 順序容器 | [\<array>](array.md)<sup>11</sup>、 [\<deque>](deque.md) 、 [\<forward_list>](forward-list.md) <sup>11</sup>、 [\<list>](list.md) 、[\<vector>](vector.md) |
| 已排序的關聯容器| [\<map>](map.md), [\<set>](set.md) |
| 未排序的關聯容器 | [\<unordered_map>](unordered-map.md)<sup>11</sup>、 [\<unordered_set>](unordered-set.md) <sup>11</sup> |
| 容器配接器 | [\<queue>](queue.md), [\<stack>](stack.md) |
| 容器視圖 | [\<span>](span.md)<sup>名</sup> |
| [錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert>](cassert.md)、 [\<exception>](exception.md) 、 [\<stdexcept>](stdexcept.md) 、 [\<system_error>](system-error.md) <sup>11</sup> |
| 一般公用程式 | \<any><sup>17</sup>、 [\<bit>](bit.md) <sup>20</sup>、 [\<bitset>](bitset.md) 、 [\<cstdlib>](cstdlib.md) \<execution> <sup>17</sup>、 [\<functional>](functional.md) 、 [\<memory>](memory.md) 、 \<memory_resource> <sup>17</sup>、 \<optional> <sup>17</sup>、 [\<ratio>](ratio.md) <sup>11</sup>、 [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup>、 [\<tuple>](tuple.md) <sup>11</sup>、 [\<type_traits>](type-traits.md) <sup>11</sup>、 [\<typeindex>](typeindex.md) <sup>11</sup>、 [\<utility>](utility.md) 、 \<variant> <sup>17</sup> |
| [I/o 和格式化](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes>](cinttypes.md)<sup>11</sup>、、17、、、、、、、、、 [\<cstdio>](cstdio.md) [\<filesystem>](filesystem.md) <sup>17</sup> [\<fstream>](fstream.md) [\<iomanip>](iomanip.md) [\<ios>](ios.md) [\<iosfwd>](iosfwd.md) [\<iostream>](iostream.md) [\<istream>](istream.md) [\<ostream>](ostream.md) [\<sstream>](sstream.md) [\<streambuf>](streambuf.md) 、 [\<strstream>](strstream.md) <sup>c</sup>、 \<syncstream> <sup>20</sup> |
| 迭代器 | [\<iterator>](iterator.md) |
| 語言支援 | [\<cfloat>](cfloat.md)、 [\<climits>](climits.md) 、 [\<codecvt>](codecvt.md) <sup>11 a</sup>、 \<compare> <sup>20</sup>、 \<contract> <sup>20</sup>、 \<coroutine> <sup>20</sup>、、、、、 [\<csetjmp>](csetjmp.md) [\<csignal>](csignal.md) [\<cstdarg>](cstdarg.md) [\<cstddef>](cstddef.md) [\<cstdint>](cstdint.md) <sup>11</sup>、 [\<cstdlib>](cstdlib.md) 、 [\<exception>](exception.md) 、 [\<initializer_list>](initializer-list.md) <sup>11</sup>、、、 [\<limits>](limits.md) [\<new>](new.md) [\<typeinfo>](typeinfo.md) 、 \<version> <sup>20</sup> |
| 當地語系化 | [\<clocale>](clocale.md)、 [\<codecvt>](codecvt.md) <sup>11 a</sup>、 [\<cvt/wbuffer>](cvt-wbuffer.md) 、 [\<cvt/wstring>](cvt-wstring.md) 、[\<locale>](locale.md) |
| 數學和數值 | \<bit><sup>20</sup>、11、、、、、、 [\<cfenv>](cfenv.md) <sup>11</sup> [\<cmath>](cmath.md) [\<complex>](complex.md) [\<cstdlib>](cstdlib.md) [\<limits>](limits.md) [\<numeric>](numeric.md) [\<random>](random.md) <sup>11</sup>、 [\<ratio>](ratio.md) <sup>11</sup>、[\<valarray>](valarray.md) |
| [記憶體管理](../cpp/smart-pointers-modern-cpp.md) | [\<allocators>](allocators-header.md)、 [\<memory>](memory.md) 、 \<memory_resource> <sup>17</sup>、 [\<new>](new.md) 、 [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup> |
| 多執行緒 | [\<atomic>](atomic.md)<sup>11</sup>、 [\<condition_variable>](condition-variable.md) <sup>11</sup>、 [\<future>](future.md) <sup>11</sup>、 [\<mutex>](mutex.md) <sup>11</sup>、 [\<shared_mutex>](shared-mutex.md) <sup>14</sup>、 [\<thread>](thread.md) <sup>11</sup> |
| 範圍 | \<ranges><sup>名</sup> |
| 規則運算式 | [\<regex>](regex.md)<sup>rj-11</sup> |
| 字串和字元資料 | [\<charconv>](charconv.md)<sup>17</sup>、 [\<cctype>](cctype.md) 、 [\<cstdlib>](cstdlib.md) 、 [\<cstring>](cstring.md) 、 [\<cuchar>](cuchar.md) <sup>11</sup>、 [\<cwchar>](cwchar.md) 、 [\<cwctype>](cwctype.md) 、 [\<regex>](regex.md) <sup>11</sup>、 [\<string>](string.md) 、 [\<string_view>](string-view.md) <sup>17</sup> |
| Time | [\<chrono>](chrono.md)<sup>11</sup>、 [\<ctime>](ctime.md) |

c + + 11 標準中新增了<sup>11</sup> 。
c + + 14 標準中新增了<sup>14</sup>項。
在 c + + 17 標準中新增了<sup>17</sup> 。
已在 draft c + + 20 標準中新增<sup>20</sup>個。
已在 c + + 17 標準<sup>中淘汰。</sup>
<sup>b</sup> 已在 Draft c + + 20 標準中移除。
<sup>c</sup> 在 c + + 98 標準中已淘汰。

::: moniker-end

::: moniker range="vs-2015"

|類別|標題|
|-|-|
|[演算法](./algorithms.md)|[\<algorithm>](algorithm.md)|
|C 程式庫包裝函式|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[容器](./stl-containers.md)||
|順序容器|[\<array>](array.md), [\<deque>](deque.md), [\<forward_list>](forward-list.md), [\<list>](list.md), [\<vector>](vector.md)|
|已排序的關聯容器| [\<map>](map.md), [\<set>](set.md)|
|未排序的關聯容器|[\<unordered_map>](unordered-map.md), [\<unordered_set>](unordered-set.md)|
|介面卡容器|[\<queue>](queue.md), [\<stack>](stack.md)|
|[錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<exception>](exception.md), [\<stdexcept>](stdexcept.md), [\<system_error>](system-error.md)|
|[I/o 和格式化](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|迭代器|[\<iterator>](iterator.md)|
|當地語系化|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|數學和數值|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[記憶體管理](../cpp/smart-pointers-modern-cpp.md)|[\<allocators>](allocators-header.md), [\<memory>](memory.md), [\<new>](new.md), [\<scoped_allocator>](scoped-allocator.md)|
|多執行緒|[\<atomic>](atomic.md), [\<condition_variable>](condition-variable.md), [\<future>](future.md), [\<mutex>](mutex.md), [\<shared_mutex>](shared-mutex.md), [\<thread>](thread.md)|
|其他公用程式|[\<bitset>](bitset.md), [\<chrono>](chrono.md), [\<functional>](functional.md), [\<initializer_list>](initializer-list.md), [\<tuple>](tuple.md), [\<type_traits>](type-traits.md), [\<typeinfo>](typeinfo.md), [\<typeindex>](typeindex.md), [\<utility>](utility.md)|
|字串和字元資料|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用 c + + 程式庫標頭](using-cpp-library-headers.md)\
[C + + 標準程式庫](cpp-standard-library-reference.md)
