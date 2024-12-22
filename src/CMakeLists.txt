##
## Copyright (c) 2024 Waldemar Schneider (w-schneider1987 at web dot de)
##
## Distributed under the Boost Software License, Version 1.0.
## (See accompanying file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt)


add_library(cxx_template hello.cxx)


find_package(Boost)
find_package(SOCI)      
target_link_libraries(cxx_template PUBLIC
        SOCI::soci_sqlite3_static
        Boost::boost
)
