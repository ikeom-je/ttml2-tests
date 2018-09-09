# TTML2 Test Suites

The TTML Test Suites consists of a validation test suite and a presentation test suite. The purpose of these test suites is to demonstrate adequate implementation experience of each (designated) feature of the TTML2 specification as documented by the TTML2 Implementation Report. An ancillary purpose is to promote ineroperability between implementations.

The tests found in these test suites are limited to functionality and constraints thereof that derive directly from normative text in the TTML2 specification. While additional tests that go beyond the normative specification text might be useful, especially for interoperability testing, such tests are excluded here in principle.

## Validation Test Suite

The validation test suite is found under the `validation` directory, and is divided into two parts: (1) tests for valid content (validity tests) and (2) tests for invalid content (invalidity) tests. The result of each test can be characterized as PASS or FAIL.

A PASS result for a validity test occurs if the validator does not reject (report a validation error for) the content of the test. In contrast, a FAIL result for a validity test occurs if the validator rejects (reports a validation error for) the content of the test, in which case, such a result is deemed a _false negative_ result.

A PASS result for an invalidity test occcurs if the validator rejects (reports a validation error for) the content of the test. In contrast, a FAIL result for an invalidity test occurs if the validator does not reject (report a validation error for) the content of the test, in which case, such a result is deemed a _false positive_ result.

A validator is consider to _strictly pass_ the test suite if it does not report a false negative for any validity test. A validator is consider to _fully pass_ the test suite if it (1) strictly passes the test suite and (2) does not report a false positive for any invalidity test.

For the purpose of reporting an implementation of the validation function for a specific (designated) feature, the implementation must strictly pass all tests for that feature; however, it is not required to fully pass all tests for that feature since the TTML2 specification does not require a validator to detect all possibile invalidities, about which see [validate document](https://www.w3.org/TR/ttml2/#semantics-procedure-validate-document).

A mapping from (designated) features to specific tests is found in `validation/tests.json`.

## Presentation Test Suite

The presentation test suite is found under the `presentation` directory, and is divided into two parts: (1) tests for presenting valid content and (2) tests for presenting invalid content tests.

For tests having primarily visual presentation semantics, each presentation test is associated with a like named ZIP archive with the suffix `.expected.zip`, which contains the output of a particular reference implementation (TTPE). Each such _reference archive_ contains a manifest file and one or more image frames represented in some image format. In the present form of the reference archives, the image format is `image/svg+xml`. These image frames should **not** be construed as normative, but merely serve as a possible reference image for performing (human visual) comparisons of expected output.

