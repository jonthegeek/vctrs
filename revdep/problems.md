# arrow (22.0.0)

* GitHub: <https://github.com/apache/arrow>
* Email: <mailto:jkeane@gmail.com>
* GitHub mirror: <https://github.com/cran/arrow>

Run `revdepcheck::cloud_details(, "arrow")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
       ]
     -- child 10 type: int32
       [
         0
       ]
     > array$type
     VctrsExtensionType
     POSIXct of length 0
     > as.vector(array)
     Error in `vctrs::vec_restore()`:
     ! Corrupt `POSIXct` with unknown type list.
     ℹ In file 'type-date-time.c' at line 387.
     ℹ This is an internal error that was detected in the vctrs package.
       Please report it at <https://github.com/r-lib/vctrs/issues> with a reprex (<https://tidyverse.org/help/>) and the full backtrace.
     Backtrace:
         ▆
      1. ├─base::as.vector(array)
      2. │ ├─base::as.vector(x, mode)
      3. │ └─arrow:::as.vector.ArrowDatum(x, mode)
      4. │   └─x$as_vector()
      5. │     └─self$type$as_vector(self)
      6. │       └─vctrs::vec_restore(super$as_vector(extension_array), self$ptype())
      7. └─rlang:::stop_internal_c_lib(...)
      8.   └─rlang::abort(message, call = call, .internal = TRUE, .frame = frame)
     Execution halted
     ```

*   checking tests ... ERROR
     ```
     ...

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Error ('test-metadata.R:280:3'): Date/time type roundtrip ───────────────────
       Error in `vctrs::vec_restore(storage$as_vector(), self$ptype())`: Corrupt `POSIXct` with unknown type list.
       i In file 'type-date-time.c' at line 387.
       i This is an internal error that was detected in the vctrs package.
         Please report it at <https://github.com/r-lib/vctrs/issues> with a reprex (<https://tidyverse.org/help/>) and the full backtrace.
       Backtrace:
            ▆
         1. ├─arrow:::expect_equal_data_frame(rb, example_with_times) at test-metadata.R:280:3
         2. │ ├─arrow:::expect_equal(as.data.frame(x), as.data.frame(y), ...) at ./helper-expectation.R:24:3
         3. │ │ └─base::inherits(object, "ArrowObject") at ./helper-expectation.R:35:3
         4. │ ├─base::as.data.frame(x)
         5. │ └─arrow:::as.data.frame.ArrowTabular(x)
         6. │   └─x$to_data_frame()
         7. │     └─arrow:::RecordBatch__to_dataframe(self, use_threads = option_use_threads())
         8. ├─arrow (local) `<fn>`(`<ChnkdArr>`)
         9. │ └─vctrs::vec_restore(storage$as_vector(), self$ptype())
        10. └─rlang:::stop_internal_c_lib(...)
        11.   └─rlang::abort(message, call = call, .internal = TRUE, .frame = frame)

       [ FAIL 1 | WARN 0 | SKIP 85 | PASS 6759 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# blob (1.2.4)

* GitHub: <https://github.com/tidyverse/blob>
* Email: <mailto:kirill@cynkra.com>
* GitHub mirror: <https://github.com/cran/blob>

Run `revdepcheck::cloud_details(, "blob")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
       Running ‘testthat.R’
     Running the tests in ‘tests/testthat.R’ failed.
     Complete output:
       > library(testthat)
       > library(blob)
       >
       > test_check("blob")
       Saving _problems/test-accessors-39.R
       [ FAIL 1 | WARN 0 | SKIP 3 | PASS 35 ]

       ══ Skipped tests (3) ═══════════════════════════════════════════════════════════
       • On CRAN (3): 'test-format.R:11:3', 'test-format.R:35:3', 'test-format.R:59:3'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Failure ('test-accessors.R:39:3'): can insert raw or NULL ───────────────────
       Expected `x` to equal `blob(as.raw(0), as.raw(0), NULL, NULL)`.
       Differences:
       Component 3: Modes: raw, NULL
       Component 3: Lengths: 1, 0
       Component 3: target is raw, current is NULL

       [ FAIL 1 | WARN 0 | SKIP 3 | PASS 35 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# datetimeoffset (1.0.0)

* GitHub: <https://github.com/trevorld/r-datetimeoffset>
* Email: <mailto:trevor.l.davis@gmail.com>
* GitHub mirror: <https://github.com/cran/datetimeoffset>

Run `revdepcheck::cloud_details(, "datetimeoffset")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
     + }
     Loading required package: lubridate

     Attaching package: ‘lubridate’

     The following objects are masked from ‘package:base’:

         date, intersect, setdiff, union

     `isoyear(dto)`:  2025
     `epiyear(dto)`:  2025
     `semester(dto)`:  2
     `quarter(dto)`:  4
     `week(dto)`:  51
     `isoweek(dto)`:  51
     `epiweek(dto)`:  51
     `wday(dto)`:  6
     `qday(dto)`:  80
     `yday(dto)`:  353
     `am(dto)`:  TRUE
     `pm(dto)`:  FALSE
     `days_in_month(dto)`:  31
     Error in as.POSIXlt(x)$isdst : $ operator is invalid for atomic vectors
     Calls: cat -> dst -> dst.default
     Execution halted
     ```

*   checking tests ... ERROR
     ```
     ...

       ══ Skipped tests (2) ═══════════════════════════════════════════════════════════
       • On CRAN (2): 'test-format.r:127:5', 'test-leap-seconds.r:12:5'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Error ('test-extractors.r:28:5'): lubridate extractors functions ────────────
       Error in `as.POSIXlt(x)$isdst`: $ operator is invalid for atomic vectors
       Backtrace:
           ▆
        1. ├─testthat::expect_equal(lubridate::dst(dto), FALSE) at test-extractors.r:28:5
        2. │ └─testthat::quasi_label(enquo(object), label)
        3. │   └─rlang::eval_bare(expr, quo_get_env(quo))
        4. ├─lubridate::dst(dto)
        5. └─lubridate:::dst.default(dto)
       ── Failure ('test-from-datetimeoffset.r:132:5'): as.POSIXlt() ──────────────────
       Expected `format(as.POSIXlt(dtl), digits = 6L)` to equal "12016-02-19 10:10:10.123456".
       Differences:
       `actual`:   "12016-02-19 10:10:10.123474"
       `expected`: "12016-02-19 10:10:10.123456"


       [ FAIL 2 | WARN 0 | SKIP 2 | PASS 591 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# densityarea (0.1.1)

* GitHub: <https://github.com/JoFrhwld/densityarea>
* Email: <mailto:jofrhwld@gmail.com>
* GitHub mirror: <https://github.com/cran/densityarea>

Run `revdepcheck::cloud_details(, "densityarea")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
     +                        as_sf = TRUE)) |>
     +   st_sf() ->
     +   s01_areas_sf
     Error in `reframe()`:
     ℹ In argument: `density_area(log_F2, log_F1, probs = ppoints(10), as_sf
       = TRUE)`.
     Caused by error in `vec_c()`:
     ! `proxy` of type `list` incompatible with `value` proxy of type `double`.
     ℹ In file 'slice-assign.c' at line 254.
     ℹ This is an internal error that was detected in the vctrs package.
       Please report it at <https://github.com/r-lib/vctrs/issues> with a reprex (<https://tidyverse.org/help/>) and the full backtrace.
     Backtrace:
          ▆
       1. ├─sf::st_sf(...)
       2. ├─dplyr::reframe(...)
       3. ├─dplyr:::reframe.data.frame(...)
       4. │ └─dplyr:::summarise_cols(.data, dplyr_quosures(...), by, "reframe")
       5. │   ├─base::withCallingHandlers(...)
       6. │   └─dplyr:::map(quosures, summarise_eval_one, mask = mask)
       7. │     └─base::lapply(.x, .f, ...)
       8. │       └─dplyr (local) FUN(X[[i]], ...)
       9. │         └─vctrs::vec_c(!!!chunks_k, .ptype = types_k)
      10. └─rlang:::stop_internal_c_lib(...)
      11.   └─rlang::abort(message, call = call, .internal = TRUE, .frame = frame)
     Execution halted
     ```

# diceR (3.1.0)

* GitHub: <https://github.com/AlineTalhouk/diceR>
* Email: <mailto:dchiu@bccrc.ca>
* GitHub mirror: <https://github.com/cran/diceR>

Run `revdepcheck::cloud_details(, "diceR")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       > # It is recommended that you do not modify it.
       > #
       > # Where should you do additional test configuration?
       > # Learn more about the roles of various files in:
       > # * https://r-pkgs.org/testing-design.html#sec-tests-files-overview
       > # * https://testthat.r-lib.org/articles/special-files.html
       >
       > library(testthat)
       > library(diceR)
       >
       > test_check("diceR")
       Saving _problems/test-consensus_combine-52.R
       [ FAIL 1 | WARN 0 | SKIP 0 | PASS 113 ]

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Error ('test-consensus_combine.R:51:3'): reweighing (potentially) replicates each slice of algorithm ──
       <purrr_error_indexed/rlang_error/error/condition>
       Error in `purrr::map(k, consensus_trim, E = E, ii = ii, k.method = k.method, reweigh = reweigh, n = n)`: i In index: 1.
       Caused by error in `list_flatten()`:
       ! `x` must be a node.

       [ FAIL 1 | WARN 0 | SKIP 0 | PASS 113 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# easycensus (1.1.3)

* GitHub: <https://github.com/CoryMcCartan/easycensus>
* Email: <mailto:mccartan@psu.edu>
* GitHub mirror: <https://github.com/cran/easycensus>

Run `revdepcheck::cloud_details(, "easycensus")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       > test_check("easycensus")
       Saving _problems/test-estimate-57.R
       [ FAIL 1 | WARN 0 | SKIP 2 | PASS 29 ]

       ══ Skipped tests (2) ═══════════════════════════════════════════════════════════
       • Census API not available (2): 'test-get_table.R:2:5', 'test-get_table.R:12:5'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Error ('test-estimate.R:57:5'): math works ──────────────────────────────────
       Error in `vec_c(...)`: `proxy` of type `double` incompatible with `value` proxy of type `integer`.
       i In file 'slice-assign.c' at line 254.
       i This is an internal error that was detected in the vctrs package.
         Please report it at <https://github.com/r-lib/vctrs/issues> with a reprex (<https://tidyverse.org/help/>) and the full backtrace.
       Backtrace:
           ▆
        1. ├─vctrs:::Summary.vctrs_vctr(`<est>`, na.rm = FALSE) at test-estimate.R:57:5
        2. │ ├─vctrs::vec_math(.Generic, vec_c(...), na.rm = na.rm)
        3. │ └─vctrs::vec_c(...)
        4. └─rlang:::stop_internal_c_lib(...)
        5.   └─rlang::abort(message, call = call, .internal = TRUE, .frame = frame)

       [ FAIL 1 | WARN 0 | SKIP 2 | PASS 29 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# fabletools (0.5.1)

* GitHub: <https://github.com/tidyverts/fabletools>
* Email: <mailto:mail@mitchelloharawild.com>
* GitHub mirror: <https://github.com/cran/fabletools>

Run `revdepcheck::cloud_details(, "fabletools")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       Saving _problems/test-graphics-309.R
       [ FAIL 2 | WARN 0 | SKIP 0 | PASS 288 ]

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Error ('test-graphics.R:249:3'): autoplot.fbl_ts() ──────────────────────────
       Error in `fbl_mv$.mean[, "fdeaths"]`: no 'dimnames' attribute for array
       Backtrace:
           ▆
        1. ├─testthat::expect_equal(...) at test-graphics.R:249:3
        2. │ └─testthat::quasi_label(enquo(expected), expected.label)
        3. │   └─rlang::eval_bare(expr, quo_get_env(quo))
        4. └─fbl_mv[[".mean_fdeaths"]] %||% fbl_mv$.mean[, "fdeaths"]
       ── Error ('test-graphics.R:306:3'): autolayer.fbl_ts() ─────────────────────────
       Error in `fbl_mv$.mean[, "fdeaths"]`: no 'dimnames' attribute for array
       Backtrace:
           ▆
        1. ├─testthat::expect_equal(...) at test-graphics.R:306:3
        2. │ └─testthat::quasi_label(enquo(expected), expected.label)
        3. │   └─rlang::eval_bare(expr, quo_get_env(quo))
        4. └─fbl_mv[[".mean_fdeaths"]] %||% fbl_mv$.mean[, "fdeaths"]

       [ FAIL 2 | WARN 0 | SKIP 0 | PASS 288 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# feisr (1.3.0)

* GitHub: <https://github.com/ruettenauer/feisr>
* Email: <mailto:ruettenauer@sowi.uni-kl.de>
* GitHub mirror: <https://github.com/cran/feisr>

Run `revdepcheck::cloud_details(, "feisr")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     Running examples in ‘feisr-Ex.R’ failed
     The error most likely occurred in:

     > ### Name: detrend
     > ### Title: Detrend data by individual slopes
     > ### Aliases: detrend
     >
     > ### ** Examples
     >
     > data("mwp", package = "feisr")
     >
     > # Detrend entire data.frame
     > mwp_det <- detrend(data = mwp, slopes = c("exp", "expq"), id = "id")
     Error in `list_flatten()`:
     ! `x` must be a list, not a list matrix.
     Backtrace:
         ▆
      1. ├─feisr::detrend(data = mwp, slopes = c("exp", "expq"), id = "id")
      2. │ └─dplyr::bind_rows(rbind(dhat), .id = NULL)
      3. │   └─dplyr:::list_flatten(dots, fn = is_flattenable)
      4. │     └─vctrs::obj_check_list(x)
      5. └─vctrs:::stop_non_list_type(x, y, z)
      6.   └─cli::cli_abort(...)
      7.     └─rlang::abort(...)
     Execution halted
     ```

*   checking tests ... ERROR
     ```
     ...
       Backtrace:
           ▆
        1. ├─feisr::feis(...) at test_slopes.R:14:1
        2. │ └─dplyr::bind_rows(rbind(dhat), .id = NULL)
        3. │   └─dplyr:::list_flatten(dots, fn = is_flattenable)
        4. │     └─vctrs::obj_check_list(x)
        5. └─vctrs:::stop_non_list_type(x, y, z)
        6.   └─cli::cli_abort(...)
        7.     └─rlang::abort(...)
       ── Error ('test_weights.R:19:1'): (code run outside of `test_that()`) ──────────
       Error in `list_flatten(dots, fn = is_flattenable)`: `x` must be a list, not a list matrix.
       Backtrace:
           ▆
        1. ├─feisr::feis(...) at test_weights.R:19:1
        2. │ └─dplyr::bind_rows(rbind(dhat), .id = NULL)
        3. │   └─dplyr:::list_flatten(dots, fn = is_flattenable)
        4. │     └─vctrs::obj_check_list(x)
        5. └─vctrs:::stop_non_list_type(x, y, z)
        6.   └─cli::cli_abort(...)
        7.     └─rlang::abort(...)

       [ FAIL 9 | WARN 0 | SKIP 0 | PASS 0 ]
       Error:
       ! Test failures.
       Execution halted
     ```

*   checking re-building of vignette outputs ... ERROR
     ```
     Error(s) in re-building vignettes:
       ...
     --- re-building ‘feisr-vignette.Rmd’ using rmarkdown

     Quitting from feisr-vignette.Rmd:81-84 [feis0]
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     NULL
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

     Error: processing vignette 'feisr-vignette.Rmd' failed with diagnostics:
     `x` must be a list, not a list matrix.
     --- failed re-building ‘feisr-vignette.Rmd’

     SUMMARY: processing the following file failed:
       ‘feisr-vignette.Rmd’

     Error: Vignette re-building failed.
     Execution halted
     ```

# fmesher (0.6.1)

* GitHub: <https://github.com/inlabru-org/fmesher>
* Email: <mailto:finn.lindgren@gmail.com>
* GitHub mirror: <https://github.com/cran/fmesher>

Run `revdepcheck::cloud_details(, "fmesher")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
       Running ‘testthat.R’
     Running the tests in ‘tests/testthat.R’ failed.
     Complete output:
       > library(testthat)
       > library(fmesher)
       >
       > test_check("fmesher")
       Starting 2 test processes.
       Saving _problems/test-01-integration-181.R
       [ FAIL 1 | WARN 0 | SKIP 0 | PASS 283 ]

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Failure ('test-01-integration.R:178:3'): Conversion of whole 2D mesh to integration points ──
       Expected `colnames(ips)` to equal `c("weight", ".block", "geometry", ".block_origin")`.
       Differences:
       `actual`:   "weight" ".block" ".block_origin" "geometry"
       `expected`: "weight" ".block" "geometry"      ".block_origin"


       [ FAIL 1 | WARN 0 | SKIP 0 | PASS 283 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# ggstats (0.11.0)

* GitHub: <https://github.com/larmarange/ggstats>
* Email: <mailto:joseph@larmarange.net>
* GitHub mirror: <https://github.com/cran/ggstats>

Run `revdepcheck::cloud_details(, "ggstats")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
       4. │ └─ggplot2 (local) `ggplot_gtable.ggplot2::ggplot_built`(data)
       5. │   └─ggplot2:::by_layer(...)
       6. │     ├─rlang::try_fetch(...)
       7. │     │ ├─base::tryCatch(...)
       8. │     │ │ └─base (local) tryCatchList(expr, classes, parentenv, handlers)
       9. │     │ │   └─base (local) tryCatchOne(expr, names, parentenv, handlers[[1L]])
      10. │     │ │     └─base (local) doTryCatch(return(expr), name, parentenv, handler)
      11. │     │ └─base::withCallingHandlers(...)
      12. │     └─ggplot2 (local) f(l = layers[[i]], d = data[[i]])
      13. │       └─l$draw_geom(d, layout)
      14. │         └─ggplot2 (local) draw_geom(..., self = self)
      15. │           └─self$geom$draw_layer(...)
      16. │             └─ggplot2 (local) draw_layer(..., self = self)
      17. │               └─base::lapply(...)
      18. │                 └─ggplot2 (local) FUN(X[[i]], ...)
      19. │                   ├─rlang::inject(self$draw_panel(data, panel_params, coord, !!!params))
      20. │                   └─self$draw_panel(...)
      21. │                     └─ggstats (local) draw_panel(...)
      22. │                       └─dplyr::bind_rows(...)
      23. │                         └─dplyr:::list_flatten(dots, fn = is_flattenable)
      24. │                           └─vctrs::obj_check_list(x)
      25. └─vctrs:::stop_non_list_type(x, y, z)
      26.   └─cli::cli_abort(...)
      27.     └─rlang::abort(...)
     Execution halted
     ```

*   checking tests ... ERROR
     ```
     ...
       [ FAIL 1 | WARN 0 | SKIP 21 | PASS 17 ]

       ══ Skipped tests (21) ══════════════════════════════════════════════════════════
       • On CRAN (21): 'test-geom_connector.R:2:3', 'test-geom_stripped.R:2:3',
         'test-ggcascade.R:2:3', 'test-ggcoef_model.R:2:3',
         'test-ggcoef_model.R:163:3', 'test-ggcoef_model.R:229:3',
         'test-ggcoef_model.R:272:3', 'test-ggcoef_model.R:308:3',
         'test-ggcoef_model.R:363:3', 'test-ggcoef_model.R:454:3',
         'test-gglikert.R:2:3', 'test-position_likert.R:2:3',
         'test-position_likert.R:92:1', 'test-stat_cross.R:2:3',
         'test-stat_prop.R:2:3', 'test-stat_prop.R:66:3', 'test-stat_prop.R:79:3',
         'test-stat_prop.R:96:3', 'test-stat_prop.R:122:3',
         'test-stat_weighted_mean.R:2:3', 'test_ggsurvey.R:2:3'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Error ('test-stat_prop.R:170:3'): geom_prop_bar() & geom_prop_text() & geom_prop_connector() ──
       Error in `geom_bar_connector(mapping = mapping, data = data, position = position, complete = complete, default_by = default_by, stat = StatPropProp, width = width, ...)`: Problem while converting geom to grob.
       i Error occurred in the 3rd layer.
       Caused by error in `list_flatten()`:
       ! `x` must be a list, not a list 1D array.

       [ FAIL 1 | WARN 0 | SKIP 21 | PASS 17 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# ipumsr (0.9.0)

* GitHub: <https://github.com/ipums/ipumsr>
* Email: <mailto:ipums+cran@umn.edu>
* GitHub mirror: <https://github.com/cran/ipumsr>

Run `revdepcheck::cloud_details(, "ipumsr")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       > library(ipumsr)
       >
       > test_check("ipumsr")
       Saving _problems/test_shape_read-33.R
       [ FAIL 1 | WARN 0 | SKIP 6 | PASS 882 ]

       ══ Skipped tests (6) ═══════════════════════════════════════════════════════════
       • On CRAN (6): 'test_api_helpers.R:3:1', 'test_api_helpers.R:23:1',
         'test_micro_chunked.R:24:3', 'test_read_agg.R:7:1', 'test_read_agg.R:372:1',
         'test_shape_read.R:81:1'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Failure ('test_shape_read.R:30:3'): Can row bind multiple sf files ──────────
       Expected `dplyr::bind_rows(shp2, shp3)` to be identical to `dplyr::select(shp, -"layer")`.
       Differences:
       `attr(actual$geometry, 'classes')` is a character vector ('GEOMETRYCOLLECTION', 'GEOMETRYCOLLECTION', 'GEOMETRYCOLLECTION', 'GEOMETRYCOLLECTION', 'GEOMETRYCOLLECTION', ...)
       `attr(expected$geometry, 'classes')` is absent


       [ FAIL 1 | WARN 0 | SKIP 6 | PASS 882 ]
       Error:
       ! Test failures.
       Warning message:
       `check_cassette_names()` was deprecated in vcr 2.0.0.
       Execution halted
     ```

# merTools (0.6.3)

* GitHub: <https://github.com/jknowles/merTools>
* Email: <mailto:jared@civilytics.com>
* GitHub mirror: <https://github.com/cran/merTools>

Run `revdepcheck::cloud_details(, "merTools")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     Running examples in ‘merTools-Ex.R’ failed
     The error most likely occurred in:

     > ### Name: REsim
     > ### Title: Simulate random effects from merMod 'REsim' simulates random
     > ###   effects from merMod object posterior distributions
     > ### Aliases: REsim
     >
     > ### ** Examples
     >
     > require(lme4)
     > m2 <- lmer(Reaction ~ Days + (Days | Subject), sleepstudy)
     > re2 <- REsim(m2, 25)
     Error in `list_flatten()`:
     ! `x` must be a list, not a list matrix.
     Backtrace:
         ▆
      1. ├─merTools::REsim(m2, 25)
      2. │ └─dplyr::bind_rows(zed)
      3. │   └─dplyr:::list_flatten(dots, fn = is_flattenable)
      4. │     └─vctrs::obj_check_list(x)
      5. └─vctrs:::stop_non_list_type(x, y, z)
      6.   └─cli::cli_abort(...)
      7.     └─rlang::abort(...)
     Execution halted
     ```

*   checking tests ... ERROR
     ```
     ...
         'test-helpers.R:6:3', 'test-helpers.R:23:3', 'test-helpers.R:37:3',
         'test-helpers.R:72:3', 'test-helpers.R:90:3', 'test-helpers.R:124:3',
         'test-merModList.R:10:3', 'test-merModList.R:46:3', 'test-merModList.R:72:3',
         'test-merModList.R:128:3'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Error ('test-merExtract.R:88:3'): REsim produces data.frames ────────────────
       Error in `list_flatten(dots, fn = is_flattenable)`: `x` must be a list, not a list matrix.
       Backtrace:
            ▆
         1. ├─testthat::expect_s3_class(REsim(lmerSlope1, n.sims = 100), "data.frame") at test-merExtract.R:88:3
         2. │ └─testthat::quasi_label(enquo(object))
         3. │   └─rlang::eval_bare(expr, quo_get_env(quo))
         4. ├─merTools::REsim(lmerSlope1, n.sims = 100)
         5. │ └─dplyr::bind_rows(zed)
         6. │   └─dplyr:::list_flatten(dots, fn = is_flattenable)
         7. │     └─vctrs::obj_check_list(x)
         8. └─vctrs:::stop_non_list_type(x, y, z)
         9.   └─cli::cli_abort(...)
        10.     └─rlang::abort(...)

       [ FAIL 1 | WARN 0 | SKIP 12 | PASS 234 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# move2 (0.4.5)

* Email: <mailto:b.kranstauber@uva.nl>
* GitHub mirror: <https://github.com/cran/move2>

Run `revdepcheck::cloud_details(, "move2")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
         5. │   └─testthat:::quasi_capture(...)
         6. │     ├─testthat (local) .capture(...)
         7. │     │ └─base::withCallingHandlers(...)
         8. │     └─rlang::eval_bare(quo_get_expr(.quo), quo_get_env(.quo))
         9. ├─move2::mt_stack(...)
        10. │ └─dplyr::bind_rows(dots)
        11. │   └─vctrs::vec_rbind(!!!dots, .names_to = .id, .error_call = current_env())
        12. │     └─vctrs (local) `<fn>`()
        13. │       └─vctrs (local) vec_ptype2.sf.sf(...)
        14. │         └─vctrs:::sf_ptype2(x, y, ...)
        15. │           └─vctrs::df_ptype2(x, y, ...)
        16. └─vctrs (local) `<fn>`()
        17.   └─vctrs::vec_default_ptype2(...)
        18.     ├─base::withRestarts(...)
        19.     │ └─base (local) withOneRestart(expr, restarts[[1L]])
        20.     │   └─base (local) doWithOneRestart(return(expr), restart)
        21.     └─vctrs::stop_incompatible_type(...)
        22.       └─vctrs:::stop_incompatible(...)
        23.         └─vctrs:::stop_vctrs(...)
        24.           └─rlang::abort(message, class = c(class, "vctrs_error"), ..., call = call)

       [ FAIL 3 | WARN 0 | SKIP 17 | PASS 749 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# myTAI (2.3.4)

* GitHub: <https://github.com/drostlab/myTAI>
* Email: <mailto:hajk-georg.drost@tuebingen.mpg.de>
* GitHub mirror: <https://github.com/cran/myTAI>

Run `revdepcheck::cloud_details(, "myTAI")` for more info

## Newly broken

*   checking re-building of vignette outputs ... ERROR
     ```
     Error(s) in re-building vignettes:
     --- re-building ‘myTAI.Rmd’ using rmarkdown
     ```

# nanoarrow (0.7.0-2)

* GitHub: <https://github.com/apache/arrow-nanoarrow>
* Email: <mailto:dewey@dunnington.ca>
* GitHub mirror: <https://github.com/cran/nanoarrow>

Run `revdepcheck::cloud_details(, "nanoarrow")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
     ! Can't create Array<float64()> from object of type data.frame
     Backtrace:
          ▆
       1. ├─(if (getRversion() >= "3.4") withAutoprint else force)(...)
       2. │ └─base::source(...)
       3. │   ├─base::withVisible(eval(ei, envir))
       4. │   └─base::eval(ei, envir)
       5. │     └─base::eval(ei, envir)
       6. ├─nanoarrow::as_nanoarrow_array(vctr, schema = na_vctrs(vctr))
       7. ├─nanoarrow:::as_nanoarrow_array.POSIXlt(vctr, schema = na_vctrs(vctr))
       8. │ ├─nanoarrow::as_nanoarrow_array_extension(spec, x, ..., schema = schema)
       9. │ └─nanoarrow:::as_nanoarrow_array_extension.nanoarrow_extension_spec_vctrs(...)
      10. │   ├─nanoarrow::as_nanoarrow_array(vctrs::vec_data(x), schema = storage_schema)
      11. │   └─nanoarrow:::as_nanoarrow_array.data.frame(...)
      12. │     └─nanoarrow:::as_nanoarrow_array.default(x, ..., schema = schema)
      13. └─nanoarrow:::as_nanoarrow_array_from_c(`<df[,11]>`, `<nnrrw_sc>`)
      14.   ├─nanoarrow::as_nanoarrow_array(x, schema = schema, .from_c = TRUE)
      15.   └─nanoarrow:::as_nanoarrow_array.data.frame(...)
      16.     └─nanoarrow:::as_nanoarrow_array.default(x, ..., schema = schema)
      17.       ├─nanoarrow::as_nanoarrow_array(arrow::as_arrow_array(x, type = arrow::as_data_type(schema)))
      18.       ├─arrow::as_arrow_array(x, type = arrow::as_data_type(schema))
      19.       └─arrow:::as_arrow_array.data.frame(x, type = arrow::as_data_type(schema))
      20.         └─arrow:::stop_cant_convert_array(x, type)
      21.           └─rlang::abort(...)
     Execution halted
     ```

*   checking tests ... ERROR
     ```
     ...
       ── Error ('test-extension-vctrs.R:42:5'): vctrs extension type can roundtrip built-in vector types ──
       Error in `arrow::as_arrow_array(x, type = arrow::as_data_type(schema))`: Can't create Array<float64()> from object of type data.frame
       Backtrace:
            ▆
         1. ├─nanoarrow::as_nanoarrow_array(vctr, schema = schema) at test-extension-vctrs.R:42:5
         2. ├─nanoarrow:::as_nanoarrow_array.POSIXlt(vctr, schema = schema)
         3. │ ├─nanoarrow::as_nanoarrow_array_extension(spec, x, ..., schema = schema)
         4. │ └─nanoarrow:::as_nanoarrow_array_extension.nanoarrow_extension_spec_vctrs(...)
         5. │   ├─nanoarrow::as_nanoarrow_array(vctrs::vec_data(x), schema = storage_schema)
         6. │   └─nanoarrow:::as_nanoarrow_array.data.frame(...)
         7. │     └─nanoarrow:::as_nanoarrow_array.default(x, ..., schema = schema)
         8. └─nanoarrow:::as_nanoarrow_array_from_c(`<df[,11]>`, `<nnrrw_sc>`)
         9.   ├─nanoarrow::as_nanoarrow_array(x, schema = schema, .from_c = TRUE)
        10.   └─nanoarrow:::as_nanoarrow_array.data.frame(...)
        11.     └─nanoarrow:::as_nanoarrow_array.default(x, ..., schema = schema)
        12.       ├─nanoarrow::as_nanoarrow_array(arrow::as_arrow_array(x, type = arrow::as_data_type(schema)))
        13.       ├─arrow::as_arrow_array(x, type = arrow::as_data_type(schema))
        14.       └─arrow:::as_arrow_array.data.frame(x, type = arrow::as_data_type(schema))
        15.         └─arrow:::stop_cant_convert_array(x, type)
        16.           └─rlang::abort(...)

       [ FAIL 1 | WARN 0 | SKIP 8 | PASS 1588 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# nswgeo (0.5.0)

* GitHub: <https://github.com/cidm-ph/nswgeo>
* Email: <mailto:Carl.Suster@health.nsw.gov.au>
* GitHub mirror: <https://github.com/cran/nswgeo>

Run `revdepcheck::cloud_details(, "nswgeo")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
       5. │   └─ggplot2:::by_layer(...)
       6. │     ├─rlang::try_fetch(...)
       7. │     │ ├─base::tryCatch(...)
       8. │     │ │ └─base (local) tryCatchList(expr, classes, parentenv, handlers)
       9. │     │ │   └─base (local) tryCatchOne(expr, names, parentenv, handlers[[1L]])
      10. │     │ │     └─base (local) doTryCatch(return(expr), name, parentenv, handler)
      11. │     │ └─base::withCallingHandlers(...)
      12. │     └─ggplot2 (local) f(l = layers[[i]], d = data[[i]])
      13. │       └─l$compute_geom_2(d, theme = plot@theme)
      14. │         └─ggplot2 (local) compute_geom_2(..., self = self)
      15. │           └─ggproto_parent(Layer, self)$compute_geom_2(data, params, ...)
      16. │             └─ggplot2 (local) compute_geom_2(..., self = self)
      17. │               └─self$geom$use_defaults(...)
      18. │                 └─ggplot2 (local) use_defaults(..., self = self)
      19. │                   └─vctrs::vec_c(points, lines, others, collections)
      20. │                     └─vctrs (local) `<fn>`()
      21. │                       ├─vctrs:::vec_restore_dispatch(x = x, to = to)
      22. │                       └─sf:::vec_restore.sfc(x = x, to = to)
      23. │                         └─sf::st_sfc(x, crs = st_crs(to), precision = st_precision(to))
      24. └─base::.handleSimpleError(...)
      25.   └─rlang (local) h(simpleError(msg, call))
      26.     └─handlers[[1L]](cnd)
      27.       └─cli::cli_abort(...)
      28.         └─rlang::abort(...)
     Execution halted
     ```

# orderly (2.0.0)

* GitHub: <https://github.com/mrc-ide/orderly>
* Email: <mailto:rich.fitzjohn@gmail.com>
* GitHub mirror: <https://github.com/cran/orderly>

Run `revdepcheck::cloud_details(, "orderly")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Error ('test-util.R:676:3'): replace_ragged with an empty result preserves the input's type ──
       <vctrs_error_cast/vctrs_error_incompatible_type/vctrs_error_incompatible/vctrs_error/rlang_error/error/condition>
       Error in `vctrs::list_unchop(ret, ptype = vctrs::vec_ptype(x))`: Can't convert `x[[1]]` <double> to <character>.
       Backtrace:
            ▆
         1. ├─orderly:::replace_ragged("foo", 1, list(numeric(0))) at test-util.R:676:3
         2. │ └─vctrs::list_unchop(ret, ptype = vctrs::vec_ptype(x))
         3. └─vctrs (local) `<fn>`()
         4.   └─vctrs::vec_default_cast(...)
         5.     ├─base::withRestarts(...)
         6.     │ └─base (local) withOneRestart(expr, restarts[[1L]])
         7.     │   └─base (local) doWithOneRestart(return(expr), restart)
         8.     └─vctrs::stop_incompatible_cast(...)
         9.       └─vctrs::stop_incompatible_type(...)
        10.         └─vctrs:::stop_incompatible(...)
        11.           └─vctrs:::stop_vctrs(...)
        12.             └─rlang::abort(message, class = c(class, "vctrs_error"), ..., call = call)

       [ FAIL 1 | WARN 0 | SKIP 17 | PASS 2204 ]
       Error:
       ! Test failures.
       Execution halted
       Ran 16/16 deferred expressions
     ```

# purrr (1.2.0)

* GitHub: <https://github.com/tidyverse/purrr>
* Email: <mailto:hadley@posit.co>
* GitHub mirror: <https://github.com/cran/purrr>

Run `revdepcheck::cloud_details(, "purrr")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
     > ### Name: array-coercion
     > ### Title: Coerce array to list
     > ### Aliases: array-coercion array_branch array_tree
     >
     > ### ** Examples
     >
     > # We create an array with 3 dimensions
     > x <- array(1:12, c(2, 2, 3))
     >
     > # A full margin for such an array would be the vector 1:3. This is
     > # the default if you don't specify a margin
     >
     > # Creating a branch along the full margin is equivalent to
     > # as.list(array) and produces a list of size length(x):
     > array_branch(x) |> str()
     Error in `list_flatten()`:
     ! `x` must be a node.
     Backtrace:
         ▆
      1. ├─utils::str(array_branch(x))
      2. └─purrr::array_branch(x)
      3.   └─purrr::list_flatten(apply(array, margin, list))
      4.     └─cli::cli_abort("{.arg x} must be a node.")
      5.       └─rlang::abort(...)
     Execution halted
     ```

*   checking tests ... ERROR
     ```
     ...
       Backtrace:
           ▆
        1. ├─testthat::expect_length(array_branch(x, m1), prod(dim(x)[m1])) at test-arrays.R:23:3
        2. │ └─testthat::quasi_label(enquo(object))
        3. │   └─rlang::eval_bare(expr, quo_get_env(quo))
        4. └─purrr::array_branch(x, m1)
        5.   └─purrr::list_flatten(apply(array, margin, list))
        6.     └─cli::cli_abort("{.arg x} must be a node.")
        7.       └─rlang::abort(...)
       ── Error ('test-arrays.R:30:3'): array_branch retains dimnames when going over one dimension ──
       Error in `list_flatten(apply(array, margin, list))`: `x` must be a node.
       Backtrace:
           ▆
        1. ├─testthat::expect_identical(...) at test-arrays.R:30:3
        2. │ └─testthat::quasi_label(enquo(object), label)
        3. │   └─rlang::eval_bare(expr, quo_get_env(quo))
        4. └─purrr::array_branch(x, 2:3)
        5.   └─purrr::list_flatten(apply(array, margin, list))
        6.     └─cli::cli_abort("{.arg x} must be a node.")
        7.       └─rlang::abort(...)

       [ FAIL 3 | WARN 0 | SKIP 135 | PASS 824 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# rainette (0.3.1.1)

* GitHub: <https://github.com/juba/rainette>
* Email: <mailto:julien.barnier@cnrs.fr>
* GitHub mirror: <https://github.com/cran/rainette>

Run `revdepcheck::cloud_details(, "rainette")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       ℹ In argument: `chi2 = sum(cross_groups$chi2[.data$clusters])`.
       ℹ In row 1.
       Caused by error in `cross_groups$chi2[.data$clusters]`:
       ! invalid subscript type 'list'

       [ FAIL 2 | WARN 0 | SKIP 1 | PASS 126 ]
       Deleting unused snapshots: 'plots/base-rainette-plot-measure-docprop.svg',
       'plots/base-rainette-plot-measure-frequency.svg',
       'plots/base-rainette-plot-measure-lr.svg',
       'plots/base-rainette-plot-with-free-scales.svg',
       'plots/base-rainette-plot-with-k-and-without-negative.svg',
       'plots/base-rainette-plot-with-k-n-terms-and-font-size.svg',
       'plots/base-rainette-plot.svg',
       'plots/base-rainette2-plot-measure-docprop.svg',
       'plots/base-rainette2-plot-measure-frequency.svg',
       'plots/base-rainette2-plot-measure-lr.svg',
       'plots/base-rainette2-plot-with-complete-groups.svg',
       'plots/base-rainette2-plot-with-free-scales.svg',
       'plots/base-rainette2-plot-with-k-5.svg',
       'plots/base-rainette2-plot-with-k-and-without-negative.svg',
       'plots/base-rainette2-plot-with-k-n-terms-and-font-size.svg', and
       'plots/base-rainette2-plot.svg'
       Error:
       ! Test failures.
       Execution halted
     ```

*   checking re-building of vignette outputs ... ERROR
     ```
     ...
     Caused by error in `cross_groups$chi2[.data$clusters]`:
     ! invalid subscript type 'list'
     --- failed re-building ‘introduction_en.Rmd’

     --- re-building ‘introduction_usage.Rmd’ using rmarkdown

     Quitting from introduction_usage.Rmd:186-188 [unnamed-chunk-19]
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     NULL
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

     Error: processing vignette 'introduction_usage.Rmd' failed with diagnostics:
     ℹ In index: 1.
     Caused by error in `dplyr::mutate()`:
     ℹ In argument: `chi2 = sum(cross_groups$chi2[.data$clusters])`.
     ℹ In row 1.
     Caused by error in `cross_groups$chi2[.data$clusters]`:
     ! invalid subscript type 'list'
     --- failed re-building ‘introduction_usage.Rmd’

     SUMMARY: processing the following files failed:
       ‘introduction_en.Rmd’ ‘introduction_usage.Rmd’

     Error: Vignette re-building failed.
     Execution halted
     ```

# REDCapCAST (25.3.2)

* GitHub: <https://github.com/agdamsbo/REDCapCAST>
* Email: <mailto:agdamsbo@clin.au.dk>
* GitHub mirror: <https://github.com/cran/REDCapCAST>

Run `revdepcheck::cloud_details(, "REDCapCAST")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
     Caused by error in `dplyr::if_else()`:
     ! Can't combine `true` <character> and `false` <logical>.
     Backtrace:
          ▆
       1. ├─REDCapCAST::ds2dd_detailed(dplyr::select(redcapcast_data, -dplyr::starts_with("redcap_")))
       2. │ ├─dplyr::mutate(...)
       3. │ └─dplyr:::mutate.data.frame(...)
       4. │   └─dplyr:::mutate_cols(.data, dplyr_quosures(...), by)
       5. │     ├─base::withCallingHandlers(...)
       6. │     └─dplyr:::mutate_col(dots[[i]], data, mask, new_columns)
       7. │       └─mask$eval_all_mutate(quo)
       8. │         └─dplyr (local) eval()
       9. ├─dplyr::if_else(is.na(field_label), colnames(data), field_label)
      10. │ └─dplyr:::vec_case_when(...)
      11. │   └─vctrs::vec_ptype_common(!!!everything, .ptype = ptype, .call = call)
      12. └─vctrs (local) `<fn>`()
      13.   └─vctrs::vec_default_ptype2(...)
      14.     ├─base::withRestarts(...)
      15.     │ └─base (local) withOneRestart(expr, restarts[[1L]])
      16.     │   └─base (local) doWithOneRestart(return(expr), restart)
      17.     └─vctrs::stop_incompatible_type(...)
      18.       └─vctrs:::stop_incompatible(...)
      19.         └─vctrs:::stop_vctrs(...)
      20.           └─rlang::abort(message, class = c(class, "vctrs_error"), ..., call = call)
     Execution halted
     ```

*   checking re-building of vignette outputs ... ERROR
     ```
     ...
     --- re-building ‘Database-creation.Rmd’ using rmarkdown
     --- finished re-building ‘Database-creation.Rmd’

     --- re-building ‘REDCapCAST.Rmd’ using rmarkdown
     --- finished re-building ‘REDCapCAST.Rmd’

     --- re-building ‘Shiny-app.Rmd’ using rmarkdown

     Quitting from Shiny-app.Rmd:37-42 [unnamed-chunk-4]
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     NULL
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

     Error: processing vignette 'Shiny-app.Rmd' failed with diagnostics:
     ℹ In argument: `field_label = dplyr::if_else(is.na(field_label),
       colnames(data), field_label)`.
     Caused by error in `dplyr::if_else()`:
     ! Can't combine `true` <character> and `false` <logical>.
     --- failed re-building ‘Shiny-app.Rmd’

     SUMMARY: processing the following file failed:
       ‘Shiny-app.Rmd’

     Error: Vignette re-building failed.
     Execution halted
     ```

# riskmetric (0.2.5)

* GitHub: <https://github.com/pharmaR/riskmetric>
* Email: <mailto:eli.miller@atorusresearch.com>
* GitHub mirror: <https://github.com/cran/riskmetric>

Run `revdepcheck::cloud_details(, "riskmetric")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
         2. │ └─testthat::test_dir(...)
         3. │   └─testthat:::test_files(...)
         4. │     └─testthat:::test_files_serial(...)
         5. │       └─testthat:::test_files_setup_state(...)
         6. │         └─testthat::source_test_setup(".", env)
         7. │           └─testthat::source_dir(path, "^setup.*\\.[rR]$", env = env, wrap = FALSE)
         8. │             └─base::lapply(...)
         9. │               └─testthat (local) FUN(X[[i]], ...)
        10. │                 └─testthat::source_file(...)
        11. │                   ├─base::withCallingHandlers(...)
        12. │                   └─base::eval(exprs, env)
        13. │                     └─base::eval(exprs, env)
        14. │                       └─riskmetric::pkg_ref(c("utils", "tools"), source = "pkg_install") at ./setup_test_packages.R:58:1
        15. │                         └─riskmetric::as_pkg_ref(x, ...)
        16. │                           └─vctrs::new_list_of(pkg_ref_list, ptype = pkg_ref(), class = "list_of_pkg_ref")
        17. │                             └─vctrs::vec_ptype(ptype, x_arg = "ptype")
        18. │                               └─vctrs (local) `<fn>`()
        19. │                                 ├─base::names(x = x)
        20. │                                 └─riskmetric:::names.pkg_ref(x = x)
        21. │                                   └─riskmetric:::bare_env(x, names(x))
        22. └─base::.handleSimpleError(...)
        23.   └─testthat (local) h(simpleError(msg, call))
        24.     └─cli::cli_abort(...)
        25.       └─rlang::abort(...)
       Execution halted
     ```

*   checking re-building of vignette outputs ... ERROR
     ```
     ...
     ! "environment" can only be set as the class if the object has this type; found "logical"
     ---
     Backtrace:
          ▆
       1. ├─riskmetric::pkg_assess(as_tibble(pkg_ref("riskmetric")))
       2. ├─tibble::as_tibble(pkg_ref("riskmetric"))
       3. └─riskmetric:::as_tibble.pkg_ref(pkg_ref("riskmetric"))
       4.   ├─tibble::as_tibble(...)
       5.   └─vctrs::new_list_of(list(x), ptype = pkg_ref(), class = "list_of_pkg_ref")
       6.     └─vctrs::vec_ptype(ptype, x_arg = "ptype")
       7.       └─vctrs (local) `<fn>`()
       8.         ├─base::names(x = x)
       9.         └─riskmetric:::names.pkg_ref(x = x)
      10.           └─riskmetric:::bare_env(x, names(x))
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

     Error: processing vignette 'riskmetric.Rmd' failed with diagnostics:
     "environment" can only be set as the class if the object has this type; found "logical"
     --- failed re-building ‘riskmetric.Rmd’

     SUMMARY: processing the following files failed:
       ‘extending-riskmetric.Rmd’ ‘riskmetric.Rmd’

     Error: Vignette re-building failed.
     Execution halted
     ```

# rlang (1.1.6)

* GitHub: <https://github.com/r-lib/rlang>
* Email: <mailto:lionel@posit.co>
* GitHub mirror: <https://github.com/cran/rlang>

Run `revdepcheck::cloud_details(, "rlang")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       `expected`: "<int[,2]>"

       ── Failure ('test-deparse.R:877:3'): matrices and arrays are formatted (#383) ──
       Expected `expr_deparse(mat2)` to equal "<int[,2]: 1L, 2L, 3L, 4L>".
       Differences:
       `actual`:   "<int: 1L, 2L, 3L, 4L>"
       `expected`: "<int[,2]: 1L, 2L, 3L, 4L>"

       ── Failure ('test-deparse.R:880:3'): matrices and arrays are formatted (#383) ──
       Expected `as_label(arr)` to equal "<int[,1,3]>".
       Differences:
       `actual`:   "<int>"
       `expected`: "<int[,1,3]>"

       ── Failure ('test-deparse.R:881:3'): matrices and arrays are formatted (#383) ──
       Expected `expr_deparse(arr)` to equal "<int[,1,3]: 1L, 2L, 3L>".
       Differences:
       `actual`:   "<int: 1L, 2L, 3L>"
       `expected`: "<int[,1,3]: 1L, 2L, 3L>"


       [ FAIL 7 | WARN 1 | SKIP 256 | PASS 3806 ]
       Error:
       ! Test failures.
       Execution halted
     ```

## In both

*   checking compiled code ... NOTE
     ```
     File ‘rlang/libs/rlang.so’:
       Found non-API calls to R: ‘ENCLOS’, ‘OBJECT’, ‘PRENV’, ‘PRVALUE’,
         ‘R_PromiseExpr’, ‘Rf_allocSExp’, ‘Rf_findVarInFrame3’, ‘SETLENGTH’,
         ‘SET_BODY’, ‘SET_CLOENV’, ‘SET_ENCLOS’, ‘SET_FORMALS’,
         ‘SET_GROWABLE_BIT’, ‘SET_TRUELENGTH’, ‘SET_TYPEOF’, ‘XTRUELENGTH’

     Compiled code should not call non-API entry points in R.

     See ‘Writing portable packages’ in the ‘Writing R Extensions’ manual,
     and section ‘Moving into C API compliance’ for issues with the use of
     non-API entry points.
     ```

# sf (1.0-23)

* GitHub: <https://github.com/r-spatial/sf>
* Email: <mailto:edzer.pebesma@uni-muenster.de>
* GitHub mirror: <https://github.com/cran/sf>

Run `revdepcheck::cloud_details(, "sf")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       Component "y": Attributes: < Component 3: Modes: character, list >
       Component "y": Attributes: < Component 3: names for current but not for target >
       Component "y": Attributes: < Component 3: Attributes: < target is NULL, current is list > >
       Component "y": Attributes: < Component 3: target is character, current is crs >
       Component "y": Attributes: < Component 4: Modes: list, numeric >
       Component "y": Attributes: < Component 4: names for target but not for current >
       ...
       ── Failure ('test-tidyverse.R:156:2'): bind_rows() returns type of first input ──
       Expected `out` to be identical to `exp`.
       Differences:
       Component "z": Attributes: < Names: 3 string mismatches >
       Component "z": Attributes: < Length mismatch: comparison on first 5 components >
       Component "z": Attributes: < Component "class": 1 string mismatch >
       Component "z": Attributes: < Component 3: Modes: character, list >
       Component "z": Attributes: < Component 3: names for current but not for target >
       Component "z": Attributes: < Component 3: Attributes: < target is NULL, current is list > >
       Component "z": Attributes: < Component 3: target is character, current is crs >
       Component "z": Attributes: < Component 4: Modes: list, numeric >
       Component "z": Attributes: < Component 4: names for target but not for current >
       ...

       [ FAIL 5 | WARN 4 | SKIP 64 | PASS 726 ]
       Error:
       ! Test failures.
       Execution halted
     ```

## Newly fixed

*   checking tests ... NOTE
     ```
     ...
       Running ‘sample.R’
       Comparing ‘sample.Rout’ to ‘sample.Rout.save’ ... OK
       Running ‘sfc.R’
       Comparing ‘sfc.Rout’ to ‘sfc.Rout.save’ ... OK
       Running ‘sfg.R’
       Comparing ‘sfg.Rout’ to ‘sfg.Rout.save’ ... OK
       Running ‘spatstat.R’
       Comparing ‘spatstat.Rout’ to ‘spatstat.Rout.save’ ... OK
       Running ‘stars.R’
       Comparing ‘stars.Rout’ to ‘stars.Rout.save’ ...294c294,296
     <       "nodata_value": 0
     ---
     >       "nodata_value": 0,
     >       "structural_info": {
     >         "COMPRESSOR": "{ \"blocksize\": 0, \"clevel\": 5, \"cname\": \"lz4\", \"id\": \"blosc\", \"shuffle\": 1 }"
     297c299,300
     < }[1] "{\n  \"type\": \"group\",\n  \"driver\": \"Zarr\",\n  \"name\": \"/\",\n  \"arrays\": {\n    \"ones\": {\n      \"datatype\": \"Int32\",\n      \"dimensions\": [\n        {\n          \"name\": \"dim0\",\n          \"full_name\": \"dim0\",\n          \"size\": 100\n        },\n        {\n          \"name\": \"dim1\",\n          \"full_name\": \"dim1\",\n          \"size\": 100\n        }\n      ],\n      \"dimension_size\": [\n        100,\n        100\n      ],\n      \"block_size\": [\n        50,\n        50\n      ],\n      \"nodata_value\": 0\n    }\n  }\n}"
     ---
     >   }
     > }[1] "{\n  \"type\": \"group\",\n  \"driver\": \"Zarr\",\n  \"name\": \"/\",\n  \"arrays\": {\n    \"ones\": {\n      \"datatype\": \"Int32\",\n      \"dimensions\": [\n        {\n          \"name\": \"dim0\",\n          \"full_name\": \"dim0\",\n          \"size\": 100\n        },\n        {\n          \"name\": \"dim1\",\n          \"full_name\": \"dim1\",\n          \"size\": 100\n        }\n      ],\n      \"dimension_size\": [\n        100,\n        100\n      ],\n      \"block_size\": [\n        50,\n        50\n      ],\n      \"nodata_value\": 0,\n      \"structural_info\": {\n        \"COMPRESSOR\": \"{ \\\"blocksize\\\": 0, \\\"clevel\\\": 5, \\\"cname\\\": \\\"lz4\\\", \\\"id\\\": \\\"blosc\\\", \\\"shuffle\\\": 1 }\"\n      }\n    }\n  }\n}"
       Running ‘testthat.R’
       Running ‘units.R’
       Comparing ‘units.Rout’ to ‘units.Rout.save’ ... OK
       Running ‘wkb.R’
       Comparing ‘wkb.Rout’ to ‘wkb.Rout.save’ ... OK
     ```

# skimr (2.2.1)

* GitHub: <https://github.com/ropensci/skimr>
* Email: <mailto:elin.waring@gmail.com>
* GitHub mirror: <https://github.com/cran/skimr>

Run `revdepcheck::cloud_details(, "skimr")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Failure ('test-vctrs.R:8:3'): You can bind skim_df rows ─────────────────────
       Expected `attrs$data_rows` to equal 182.
       Differences:
         `actual`: 332.0
       `expected`: 182.0

       ── Failure ('test-vctrs.R:9:3'): You can bind skim_df rows ─────────────────────
       Expected `attrs$data_cols` to equal 16.
       Differences:
         `actual`: 21.0
       `expected`: 16.0

       ── Failure ('test-vctrs.R:10:3'): You can bind skim_df rows ────────────────────
       Expected `attrs$df_name` to equal "`iris`+`mtcars`".
       Differences:
       `actual`:   "`iris`+`iris`+`mtcars`"
       `expected`: "`iris`+`mtcars`"


       [ FAIL 3 | WARN 0 | SKIP 27 | PASS 567 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# slider (0.3.3)

* GitHub: <https://github.com/r-lib/slider>
* Email: <mailto:davis@posit.co>
* GitHub mirror: <https://github.com/cran/slider>

Run `revdepcheck::cloud_details(, "slider")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       Expected `hop_index_vec(Sys.Date() + 1:5, 1:5, 1:5, 1:5, ~.x, .ptype = as.POSIXlt(Sys.Date()))` to inherit from "POSIXlt".
       Actual class: "POSIXct"/"POSIXt".
       ── Failure ('test-hop-vec.R:109:3'): .ptypes with a vec_proxy() are restored to original type ──
       Expected `hop_vec(Sys.Date() + 1:5, 1:5, 1:5, ~.x, .ptype = as.POSIXlt(Sys.Date()))` to inherit from "POSIXlt".
       Actual class: "POSIXct"/"POSIXt".
       ── Failure ('test-pslide-period-vec.R:166:3'): .ptypes with a vec_proxy() are restored to original type ──
       Expected `pslide_period_vec(...)` to inherit from "POSIXlt".
       Actual class: "POSIXct"/"POSIXt".
       ── Failure ('test-slide-index-vec.R:121:3'): .ptypes with a vec_proxy() are restored to original type ──
       Expected `slide_index_vec(Sys.Date() + 1:5, 1:5, ~.x, .ptype = as.POSIXlt(Sys.Date()))` to inherit from "POSIXlt".
       Actual class: "POSIXct"/"POSIXt".
       ── Failure ('test-slide-period-vec.R:147:3'): .ptypes with a vec_proxy() are restored to original type ──
       Expected `slide_period_vec(...)` to inherit from "POSIXlt".
       Actual class: "POSIXct"/"POSIXt".
       ── Failure ('test-slide-period2-vec.R:177:3'): .ptypes with a vec_proxy() are restored to original type ──
       Expected `slide_period2_vec(...)` to inherit from "POSIXlt".
       Actual class: "POSIXct"/"POSIXt".
       ── Failure ('test-slide-vec.R:114:3'): .ptypes with a vec_proxy() are restored to original type ──
       Expected `slide_vec(Sys.Date() + 1:5, ~.x, .ptype = as.POSIXlt(Sys.Date()))` to inherit from "POSIXlt".
       Actual class: "POSIXct"/"POSIXt".

       [ FAIL 7 | WARN 0 | SKIP 162 | PASS 1046 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# subincomeR (0.4.0)

* GitHub: <https://github.com/pablogguz/subincomeR>
* Email: <mailto:garciagp@ebrd.com>
* GitHub mirror: <https://github.com/cran/subincomeR>

Run `revdepcheck::cloud_details(, "subincomeR")` for more info

## Newly broken

*   checking re-building of vignette outputs ... ERROR
     ```
     ...

     Quitting from regional-convergence.Rmd:38-62 [unnamed-chunk-2]
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     <error/rlang_error>
     Error in `value[[3L]]()`:
     ! Failed to download the dataset. Error: cannot open URL 'https://zenodo.org/records/16313760/files/DOSE_V2.11.csv?download=1'
     ---
     Backtrace:
         ▆
      1. └─subincomeR::getDOSE(years = c(2000, 2019))
      2.   └─base::tryCatch(...)
      3.     └─base (local) tryCatchList(expr, classes, parentenv, handlers)
      4.       └─base (local) tryCatchOne(expr, names, parentenv, handlers[[1L]])
      5.         └─value[[3L]](cond)
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

     Error: processing vignette 'regional-convergence.Rmd' failed with diagnostics:
     Failed to download the dataset. Error: cannot open URL 'https://zenodo.org/records/16313760/files/DOSE_V2.11.csv?download=1'
     --- failed re-building ‘regional-convergence.Rmd’

     SUMMARY: processing the following file failed:
       ‘regional-convergence.Rmd’

     Error: Vignette re-building failed.
     Execution halted
     ```

# taxa (0.4.4)

* GitHub: <https://github.com/ropensci/taxa>
* Email: <mailto:zacharyfoster1989@gmail.com>
* GitHub mirror: <https://github.com/cran/taxa>

Run `revdepcheck::cloud_details(, "taxa")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...

       >
       > test_check("taxa")
       Saving _problems/test--taxonomy-316.R
       [ FAIL 1 | WARN 0 | SKIP 11 | PASS 408 ]

       ══ Skipped tests (11) ══════════════════════════════════════════════════════════
       • On CRAN (11): 'test--taxon.R:42:3', 'test--taxon.R:56:3',
         'test--taxon_authority.R:32:3', 'test--taxon_authority.R:39:3',
         'test--taxon_db.R:34:3', 'test--taxon_db.R:41:3', 'test--taxon_db_def.R:7:3',
         'test--taxon_id.R:40:3', 'test--taxon_id.R:47:3', 'test--taxon_rank.R:33:3',
         'test--taxonomy.R:48:3'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Failure ('test--taxonomy.R:316:3'): taxonomy objects can be combined ────────
       Expected `c(x)` to equal `x`.
       Differences:
       Component "taxa": Component "rank": Attributes: < Component "levels": Lengths: 0, 4 >
       Component "taxa": Component "rank": Attributes: < Component "levels": Component "level": Lengths (0, 4) differ (string compare on first 0) >
       Component "taxa": Component "rank": Attributes: < Component "levels": Component "order": Numeric: lengths (0, 4) differ >

       [ FAIL 1 | WARN 0 | SKIP 11 | PASS 408 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# taylor (3.2.0)

* GitHub: <https://github.com/wjakethompson/taylor>
* Email: <mailto:wjakethompson@gmail.com>
* GitHub mirror: <https://github.com/cran/taylor>

Run `revdepcheck::cloud_details(, "taylor")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       [ FAIL 1 | WARN 0 | SKIP 18 | PASS 103 ]

       ══ Skipped tests (18) ══════════════════════════════════════════════════════════
       • On CRAN (18): 'test-data-checks.R:1:1', 'test-data-checks.R:16:1',
         'test-data-checks.R:25:1', 'test-data-checks.R:62:1',
         'test-data-checks.R:79:1', 'test-data-checks.R:96:1',
         'test-data-checks.R:114:1', 'test-ggplot2-color-scales.R:3:1',
         'test-ggplot2-color-scales.R:71:1', 'test-ggplot2-color-scales.R:138:1',
         'test-ggplot2-color-scales.R:239:1', 'test-ggplot2-color-scales.R:433:1',
         'test-ggplot2-color-scales.R:500:1', 'test-ggplot2-color-scales.R:567:1',
         'test-misc.R:1:1', 'test-palette.R:1:1', 'test-palette.R:97:1',
         'test-taylor-album-palettes.R:35:1'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Failure ('test-palette.R:56:3'): casting and coercion work ──────────────────
       Expected `c(wjake_palette, album_palettes$red)` to be identical to `color_palette(...)`.
       Differences:
         `attr(actual, 'n_colors')`: 9
       `attr(expected, 'n_colors')`: 7


       [ FAIL 1 | WARN 0 | SKIP 18 | PASS 103 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# testthat (3.3.1)

* GitHub: <https://github.com/r-lib/testthat>
* Email: <mailto:hadley@posit.co>
* GitHub mirror: <https://github.com/cran/testthat>

Run `revdepcheck::cloud_details(, "testthat")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
       • file.exists(rd_path) is not TRUE (2): 'test-test-example.R:3:3',
         'test-test-example.R:12:3'

       ══ Failed tests ════════════════════════════════════════════════════════════════
       ── Failure ('test-expect-vector.R:10:3'): basic properties upheld ──────────────
       Snapshot of code has changed:
       old[3:5] vs new[3:6]
           expect_vector(y)
         Condition
           Error:
           ! `y` must be a vector, not `NULL`.
       +   i Read our FAQ about scalar types (`?vctrs::faq_error_scalar_type`) to learn more.
       * Run `testthat::snapshot_accept("expect-vector", "testthat")` to accept the change.
       * Run `testthat::snapshot_review("expect-vector", "testthat")` to review the change.

       ── Snapshots ───────────────────────────────────────────────────────────────────
       To review and process snapshots locally:
       * Locate check directory.
       * Copy 'tests/testthat/_snaps' to local package.
       * Run `testthat::snapshot_accept()` to accept all changes.
       * Run `testthat::snapshot_review()` to review all changes.
       [ FAIL 1 | WARN 0 | SKIP 177 | PASS 1065 ]
       Error:
       ! Test failures.
       Execution halted
     ```

# tibble (3.3.0)

* GitHub: <https://github.com/tidyverse/tibble>
* Email: <mailto:kirill@cynkra.com>
* GitHub mirror: <https://github.com/cran/tibble>

Run `revdepcheck::cloud_details(, "tibble")` for more info

## Newly broken

*   checking re-building of vignette outputs ... ERROR
     ```
     Error(s) in re-building vignettes:
     --- re-building ‘digits.Rmd’ using rmarkdown
     --- finished re-building ‘digits.Rmd’

     --- re-building ‘extending.Rmd’ using rmarkdown
     --- finished re-building ‘extending.Rmd’

     --- re-building ‘formats.Rmd’ using rmarkdown
     ```

# volker (3.2.0)

* GitHub: <https://github.com/strohne/volker>
* Email: <mailto:jakob.juenger@uni-muenster.de>
* GitHub mirror: <https://github.com/cran/volker>

Run `revdepcheck::cloud_details(, "volker")` for more info

## Newly broken

*   checking examples ... ERROR
     ```
     ...
       5. │       └─volker:::labs_impute(data)
       6. │         ├─dplyr::filter(...)
       7. │         ├─dplyr::filter(codebook(data), .data$item_class == "numeric")
       8. │         └─volker::codebook(data)
       9. │           ├─dplyr::mutate(...)
      10. │           ├─... %>% ...
      11. │           └─dplyr::tibble(...)
      12. │             └─tibble:::tibble_quos(xs, .rows, .name_repair)
      13. │               └─rlang::eval_tidy(xs[[j]], mask)
      14. ├─dplyr::mutate(., item_group = sub("_.*", "", .data$item_name))
      15. ├─dplyr::mutate(...)
      16. ├─dplyr::mutate(...)
      17. ├─dplyr::coalesce(item_comments, item_labels)
      18. │ └─dplyr:::vec_case_when(...)
      19. │   └─vctrs::vec_ptype_common(!!!everything, .ptype = ptype, .call = call)
      20. └─vctrs (local) `<fn>`()
      21.   └─vctrs::vec_default_ptype2(...)
      22.     ├─base::withRestarts(...)
      23.     │ └─base (local) withOneRestart(expr, restarts[[1L]])
      24.     │   └─base (local) doWithOneRestart(return(expr), restart)
      25.     └─vctrs::stop_incompatible_type(...)
      26.       └─vctrs:::stop_incompatible(...)
      27.         └─vctrs:::stop_vctrs(...)
      28.           └─rlang::abort(message, class = c(class, "vctrs_error"), ..., call = call)
     Execution halted
     ```

*   checking tests ... ERROR
     ```
     ...
         9. │       ├─dplyr::mutate(...)
        10. │       ├─... %>% ...
        11. │       └─dplyr::tibble(...)
        12. │         └─tibble:::tibble_quos(xs, .rows, .name_repair)
        13. │           └─rlang::eval_tidy(xs[[j]], mask)
        14. ├─dplyr::mutate(., item_group = sub("_.*", "", .data$item_name))
        15. ├─dplyr::mutate(...)
        16. ├─dplyr::mutate(...)
        17. ├─dplyr::coalesce(item_comments, item_labels)
        18. │ └─dplyr:::vec_case_when(...)
        19. │   └─vctrs::vec_ptype_common(!!!everything, .ptype = ptype, .call = call)
        20. └─vctrs (local) `<fn>`()
        21.   └─vctrs::vec_default_ptype2(...)
        22.     ├─base::withRestarts(...)
        23.     │ └─base (local) withOneRestart(expr, restarts[[1L]])
        24.     │   └─base (local) doWithOneRestart(return(expr), restart)
        25.     └─vctrs::stop_incompatible_type(...)
        26.       └─vctrs:::stop_incompatible(...)
        27.         └─vctrs:::stop_vctrs(...)
        28.           └─rlang::abort(message, class = c(class, "vctrs_error"), ..., call = call)

       [ FAIL 76 | WARN 0 | SKIP 3 | PASS 53 ]
       Error:
       ! Test failures.
       Execution halted
     ```

*   checking re-building of vignette outputs ... ERROR
     ```
     Error(s) in re-building vignettes:
       ...
     --- re-building ‘introduction.Rmd’ using rmarkdown

     Quitting from introduction.Rmd:174-176 [unnamed-chunk-15]
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     NULL
     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

     Error: processing vignette 'introduction.Rmd' failed with diagnostics:
     Can't combine `..1` <list> and `..2` <logical>.
     --- failed re-building ‘introduction.Rmd’

     SUMMARY: processing the following file failed:
       ‘introduction.Rmd’

     Error: Vignette re-building failed.
     Execution halted
     ```

# yamlet (1.2.5)

* GitHub: <https://github.com/bergsmat/yamlet>
* Email: <mailto:bergsmat@gmail.com>
* GitHub mirror: <https://github.com/cran/yamlet>

Run `revdepcheck::cloud_details(, "yamlet")` for more info

## Newly broken

*   checking tests ... ERROR
     ```
     ...
        1. └─testthat::expect_equal_to_reference(...) at test-classified.R:85:3
        2.   └─testthat::expect_known_value(..., update = update)
       ── Failure ('test-classified.R:87:3'): classified factors can be combined with each other and with vanilla factors ──
       `vec_c(f3, c1)` has changed from known value recorded in '132.rds'.
       Attributes: < Names: 1 string mismatch >
       Attributes: < Length mismatch: comparison on first 3 components >
       Attributes: < Component 3: Lengths (3, 1) differ (string compare on first 1) >
       Attributes: < Component 3: 1 string mismatch >
       Backtrace:
           ▆
        1. └─testthat::expect_equal_to_reference(...) at test-classified.R:87:3
        2.   └─testthat::expect_known_value(..., update = update)
       ── Failure ('test-dvec.R:148:3'): bind_rows respects column type of first argument ──
       Expected `attr(dm3$RACE, "label")` to be identical to "Race".
       Differences:
       1/1 mismatches
       x[1]: "foo"
       y[1]: "Race"
       ── Failure ('test-dvec.R:160:3'): bind_rows respects column type of first argument ──
       Expected `bind_rows(dm %>% redecorate(persistence = F), dm2) %>% decorations` to produce warnings.

       [ FAIL 5 | WARN 0 | SKIP 3 | PASS 527 ]
       Error:
       ! Test failures.
       Execution halted
     ```

## In both

*   checking re-building of vignette outputs ... WARNING
     ```
     Error(s) in re-building vignettes:
     --- re-building ‘scripted-html.Rmd’ using rmarkdown
     ```
