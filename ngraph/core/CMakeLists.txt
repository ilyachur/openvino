# ******************************************************************************
# Copyright 2017-2020 Intel Corporation
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# ******************************************************************************

add_definitions(-DIN_NGRAPH_LIBRARY)

file(GLOB_RECURSE LIBRARY_SRC ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp
                              ${CMAKE_CURRENT_SOURCE_DIR}/src/*.hpp)
file(GLOB_RECURSE PUBLIC_HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/*.hpp)

set(NGRAPH_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include/ngraph CACHE INTERNAL "")

add_subdirectory(builder)
add_subdirectory(reference)

# Create named folders for the sources within the .vcproj
# Empty name lists them directly under the .vcproj

source_group("src" FILES ${LIBRARY_SRC})
source_group("include" FILES ${PUBLIC_HEADERS})

configure_file(include/ngraph/version.in.hpp include/ngraph/version.hpp)

set (SRC
        src/axis_vector.cpp
        src/chrome_trace.cpp
        # src/validation_util.cpp
        src/distributed.cpp
        src/log.cpp
        src/util.cpp
        src/provenance.cpp
        src/ngraph.cpp
        src/axis_set.cpp
        src/node_input.cpp
        # src/opsets/opset.cpp
        src/coordinate_diff.cpp
        src/file_util.cpp
        src/pass/graph_rewrite.cpp
        # src/pass/constant_folding_quantize.cpp
        src/pass/pass.cpp
        src/pass/pass_config.cpp
        # src/pass/constant_folding_one_hot.cpp
        src/pass/validate.cpp
        # src/pass/constant_folding_logical_reduction.cpp
        # src/pass/constant_folding.cpp
        src/pass/visualize_tree.cpp
        src/pass/manager.cpp
        # src/pass/constant_folding_select.cpp
        # src/pass/constant_folding_dequantize.cpp
        # src/pass/constant_folding_gather.cpp
        # src/pass/constant_folding_convert.cpp
        # src/pass/constant_folding_arithmetic_reduction.cpp
        # src/pass/convert_fp32_to_fp16.cpp
        # src/pass/constant_folding_scatter.cpp
        # src/op/prior_box.cpp
        # src/op/gather_tree.cpp
        # src/op/squeeze.cpp
        # src/op/erf.cpp
        # src/op/not_equal.cpp
        # src/op/replace_slice.cpp
        # src/op/minimum.cpp
        src/op/op.cpp
        # src/op/or.cpp
        # src/op/acosh.cpp
        # src/op/range.cpp
        # src/op/dequantize.cpp
        # src/op/reorg_yolo.cpp
        # src/op/log.cpp
        # src/op/select.cpp
        # src/op/sum.cpp
        # src/op/sqrt.cpp
        # src/op/reshape.cpp
        # src/op/scatter_update.cpp
        # src/op/sigmoid.cpp
        # src/op/max_pool.cpp
        # src/op/prior_box_clustered.cpp
        # src/op/shuffle_channels.cpp
        # src/op/subtract.cpp
        # src/op/cum_sum.cpp
        # src/op/reduce_l2.cpp
        # src/op/avg_pool.cpp
        # src/op/softplus.cpp
        # src/op/ctc_loss.cpp
        # src/op/gather.cpp
        # src/op/group_conv.cpp
        src/op/parameter.cpp
        # src/op/broadcast.cpp
        # src/op/tanh.cpp
        # src/op/lstm_cell.cpp
        # src/op/sinh.cpp
        # src/op/util/logical_reduction_keep_dims.cpp
        # src/op/util/elementwise_args.cpp
        # src/op/util/arithmetic_reductions_keep_dims.cpp
        src/op/util/op_types.cpp
        # src/op/util/binary_elementwise_logical.cpp
        # src/op/util/recurrent_sequence.cpp
        src/op/util/attr_types.cpp
        # src/op/util/binary_elementwise_comparison.cpp
        # src/op/util/binary_elementwise_arithmetic.cpp
        # src/op/util/index_reduction.cpp
        # src/op/util/logical_reduction.cpp
        # src/op/util/activation_functions.cpp
        # src/op/util/scatter_nd_base.cpp
        # src/op/util/embeddingbag_packed_base.cpp
        # src/op/util/fused_op.cpp
        # src/op/util/rnn_cell_base.cpp
        # src/op/util/broadcast_base.cpp
        # src/op/util/unary_elementwise_arithmetic.cpp
        # src/op/util/embeddingbag_offsets_base.cpp
        # src/op/util/scatter_base.cpp
        # src/op/util/arithmetic_reduction.cpp
        # src/op/split.cpp
        # src/op/matmul.cpp
        # src/op/reduce_l1.cpp
        # src/op/not.cpp
        # src/op/scatter_nd_update.cpp
        # src/op/convert.cpp
        # src/op/variadic_split.cpp
        # src/op/elu.cpp
        # src/op/exp.cpp
        # src/op/relu.cpp
        # src/op/any.cpp
        # src/op/negative.cpp
        # src/op/quantized_convolution.cpp
        # src/op/tan.cpp
        # src/op/depth_to_space.cpp
        # src/op/assign.cpp
        # src/op/reduce_logical_or.cpp
        # src/op/embeddingbag_offsets_sum.cpp
        # src/op/slice.cpp
        # src/op/shape_of.cpp
        # src/op/floor_mod.cpp
        # src/op/stop_gradient.cpp
        # src/op/embeddingbag_packedsum.cpp
        # src/op/lrn.cpp
        # src/op/transpose.cpp
        # src/op/read_value.cpp
        # src/op/mod.cpp
        # src/op/roi_pooling.cpp
        # src/op/max.cpp
        # src/op/proposal.cpp
        # src/op/floor.cpp
        # src/op/prelu.cpp
        # src/op/quantized_dot.cpp
        # src/op/strided_slice.cpp
        # src/op/lstm_sequence.cpp
        # src/op/rnn_cell.cpp
        # src/op/reverse.cpp
        # src/op/acos.cpp
        # src/op/region_yolo.cpp
        # src/op/reduce_sum.cpp
        # src/op/less.cpp
        # src/op/detection_output.cpp
        # src/op/embedding_segments_sum.cpp
        # src/op/psroi_pooling.cpp
        # src/op/concat.cpp
        # src/op/gather_nd.cpp
        # src/op/asin.cpp
        # src/op/atan.cpp
        # src/op/non_max_suppression.cpp
        # src/op/equal.cpp
        # src/op/roi_align.cpp
        # src/op/hswish.cpp
        # src/op/multiply.cpp
        # src/op/space_to_batch.cpp
        # src/op/batch_norm.cpp
        # src/op/abs.cpp
        # src/op/power.cpp
        # src/op/mvn.cpp
        # src/op/interpolate.cpp
        # src/op/non_zero.cpp
        # src/op/round.cpp
        # src/op/and.cpp
        # src/op/squared_difference.cpp
        # src/op/pad.cpp
        # src/op/sign.cpp
        # src/op/swish.cpp
        # src/op/softmax.cpp
        # src/op/unsqueeze.cpp
        # src/op/clamp.cpp
        # src/op/topk.cpp
        # src/op/sin.cpp
        # src/op/xor.cpp
        # src/op/space_to_depth.cpp
        # src/op/tensor_iterator.cpp
        # src/op/greater_eq.cpp
        src/op/result.cpp
        # src/op/one_hot.cpp
        # src/op/reduce_logical_and.cpp
        # src/op/cos.cpp
        # src/op/deformable_psroi_pooling.cpp
        # src/op/scatter_elements_update.cpp
        # src/op/quantize.cpp
        # src/op/tile.cpp
        # src/op/bucketize.cpp
        # src/op/convert_like.cpp
        # src/op/asinh.cpp
        # src/op/reverse_sequence.cpp
        # src/op/atanh.cpp
        # src/op/ctc_greedy_decoder.cpp
        # src/op/grn.cpp
        # src/op/selu.cpp
        # src/op/add.cpp
        # src/op/less_eq.cpp
        # src/op/gelu.cpp
        src/op/constant.cpp
        # src/op/min.cpp
        # src/op/dot.cpp
        # src/op/mish.cpp
        # src/op/hard_sigmoid.cpp
        # src/op/fake_quantize.cpp
        # src/op/deformable_convolution.cpp
        # src/op/divide.cpp
        # src/op/product.cpp
        # src/op/extractimagepatches.cpp
        # src/op/convolution.cpp
        # src/op/ceiling.cpp
        # src/op/reduce_prod.cpp
        # src/op/normalize_l2.cpp
        # src/op/cosh.cpp
        # src/op/reduce_mean.cpp
        # src/op/greater.cpp
        # src/op/gru_cell.cpp
        # src/op/binary_convolution.cpp
        # src/op/batch_to_space.cpp
        # src/op/maximum.cpp
        src/node_output.cpp
        src/node.cpp
        src/itt.hpp
        src/strides.cpp
        src/runtime/aligned_buffer.cpp
        src/runtime/tensor.cpp
        src/runtime/host_tensor.cpp
        src/attribute_visitor.cpp
        src/slice_plan.cpp
        src/coordinate.cpp
        src/function.cpp
        src/type/float16.cpp
        src/type/bfloat16.cpp
        src/type/element_type.cpp
        src/shape.cpp
        src/variant.cpp
        src/descriptor/input.cpp
        src/descriptor/output.cpp
        src/descriptor/tensor.cpp
        src/dimension.cpp
        src/specialize_function.cpp
        src/rt_info.cpp
        src/factory.cpp
        src/attribute_adapter.cpp
        src/pattern/matcher.cpp
        src/pattern/op
        src/pattern/op/or.cpp
        src/pattern/op/capture.cpp
        src/pattern/op/any_output.cpp
        src/pattern/op/wrap_type.cpp
        src/pattern/op/any.cpp
        src/pattern/op/branch.cpp
        src/pattern/op/label.cpp
        src/pattern/op/skip.cpp
        src/pattern/op/pattern.cpp
        src/pattern/op/true.cpp
        src/pattern/op/any_of.cpp
        src/shape_util.cpp
        src/check.cpp
        src/graph_util.cpp
        src/interval.cpp
        src/partial_shape.cpp
        src/type.cpp
        src/env_util.cpp
        include/ngraph/specialize_function.hpp
        include/ngraph/rt_info.hpp
        include/ngraph/factory.hpp
        include/ngraph/attribute_adapter.hpp
        include/ngraph/check.hpp
        include/ngraph/shape_util.hpp
        include/ngraph/graph_util.hpp
        include/ngraph/version.in.hpp
        include/ngraph/interval.hpp
        # include/ngraph/opsets/opset4.hpp
        # include/ngraph/opsets/opset4_tbl.hpp
        # include/ngraph/opsets/opset1.hpp
        # include/ngraph/opsets/opset2.hpp
        # include/ngraph/opsets/opset3.hpp
        # include/ngraph/opsets/opset1_tbl.hpp
        # include/ngraph/opsets/opset.hpp
        # include/ngraph/opsets/opset3_tbl.hpp
        # include/ngraph/opsets/opset2_tbl.hpp
        include/ngraph/partial_shape.hpp
        include/ngraph/type.hpp
        include/ngraph/enum_names.hpp
        include/ngraph/env_util.hpp
        # include/ngraph/pass/convert_fp32_to_fp16.hpp
        include/ngraph/pass/validate.hpp
        # include/ngraph/pass/constant_folding.hpp
        include/ngraph/pass/visualize_tree.hpp
        include/ngraph/pass/manager.hpp
        include/ngraph/pass/graph_rewrite.hpp
        include/ngraph/pass/pass.hpp
        include/ngraph/pass/pass_config.hpp
        include/ngraph/function.hpp
        # include/ngraph/op/quantize.hpp
        # include/ngraph/op/scatter_elements_update.hpp
        # include/ngraph/op/deformable_psroi_pooling.hpp
        # include/ngraph/op/tile.hpp
        # include/ngraph/op/convert_like.hpp
        # include/ngraph/op/bucketize.hpp
        # include/ngraph/op/asinh.hpp
        # include/ngraph/op/atanh.hpp
        # include/ngraph/op/ctc_greedy_decoder.hpp
        # include/ngraph/op/grn.hpp
        # include/ngraph/op/selu.hpp
        # include/ngraph/op/reverse_sequence.hpp
        # include/ngraph/op/min.hpp
        # include/ngraph/op/less_eq.hpp
        # include/ngraph/op/gelu.hpp
        # include/ngraph/op/add.hpp
        include/ngraph/op/constant.hpp
        # include/ngraph/op/hard_sigmoid.hpp
        # include/ngraph/op/deformable_convolution.hpp
        # include/ngraph/op/fake_quantize.hpp
        # include/ngraph/op/dot.hpp
        # include/ngraph/op/mish.hpp
        # include/ngraph/op/divide.hpp
        # include/ngraph/op/extractimagepatches.hpp
        # include/ngraph/op/product.hpp
        # include/ngraph/op/convolution.hpp
        # include/ngraph/op/reduce_prod.hpp
        # include/ngraph/op/ceiling.hpp
        # include/ngraph/op/cosh.hpp
        # include/ngraph/op/normalize_l2.hpp
        # include/ngraph/op/util/variable.hpp
        # include/ngraph/op/util/rnn_cell_base.hpp
        # include/ngraph/op/util/broadcast_base.hpp
        # include/ngraph/op/util/unary_elementwise_arithmetic.hpp
        # include/ngraph/op/util/embeddingbag_offsets_base.hpp
        # include/ngraph/op/util/scatter_base.hpp
        # include/ngraph/op/util/arithmetic_reduction.hpp
        # include/ngraph/op/util/index_reduction.hpp
        # include/ngraph/op/util/logical_reduction.hpp
        # include/ngraph/op/util/activation_functions.hpp
        # include/ngraph/op/util/scatter_nd_base.hpp
        # include/ngraph/op/util/fused_op.hpp
        # include/ngraph/op/util/embeddingbag_packed_base.hpp
        include/ngraph/op/util/attr_types.hpp
        # include/ngraph/op/util/binary_elementwise_comparison.hpp
        # include/ngraph/op/util/eval_copy.hpp
        # include/ngraph/op/util/binary_elementwise_arithmetic.hpp
        # include/ngraph/op/util/elementwise_args.hpp
        # include/ngraph/op/util/logical_reduction_keep_dims.hpp
        # include/ngraph/op/util/arithmetic_reductions_keep_dims.hpp
        include/ngraph/op/util/op_types.hpp
        # include/ngraph/op/util/op_annotations.hpp
        # include/ngraph/op/util/binary_elementwise_logical.hpp
        # include/ngraph/op/util/recurrent_sequence.hpp
        # include/ngraph/op/reduce_mean.hpp
        # include/ngraph/op/greater.hpp
        # include/ngraph/op/maximum.hpp
        # include/ngraph/op/gru_cell.hpp
        # include/ngraph/op/batch_to_space.hpp
        # include/ngraph/op/binary_convolution.hpp
        # include/ngraph/op/roi_align.hpp
        # include/ngraph/op/atan.hpp
        # include/ngraph/op/equal.hpp
        # include/ngraph/op/non_max_suppression.hpp
        # include/ngraph/op/multiply.hpp
        # include/ngraph/op/hswish.hpp
        # include/ngraph/op/batch_norm.hpp
        # include/ngraph/op/abs.hpp
        # include/ngraph/op/space_to_batch.hpp
        # include/ngraph/op/mvn.hpp
        # include/ngraph/op/power.hpp
        # include/ngraph/op/interpolate.hpp
        # include/ngraph/op/op_version_tbl.hpp
        # include/ngraph/op/non_zero.hpp
        # include/ngraph/op/round.hpp
        # include/ngraph/op/and.hpp
        # include/ngraph/op/squared_difference.hpp
        # include/ngraph/op/swish.hpp
        # include/ngraph/op/sign.hpp
        # include/ngraph/op/pad.hpp
        # include/ngraph/op/softmax.hpp
        # include/ngraph/op/clamp.hpp
        # include/ngraph/op/unsqueeze.hpp
        # include/ngraph/op/xor.hpp
        # include/ngraph/op/sin.hpp
        # include/ngraph/op/topk.hpp
        # include/ngraph/op/space_to_depth.hpp
        # include/ngraph/op/tensor_iterator.hpp
        include/ngraph/op/result.hpp
        # include/ngraph/op/one_hot.hpp
        # include/ngraph/op/cos.hpp
        # include/ngraph/op/reduce_logical_and.hpp
        # include/ngraph/op/greater_eq.hpp
        # include/ngraph/op/variadic_split.hpp
        # include/ngraph/op/exp.hpp
        # include/ngraph/op/elu.hpp
        # include/ngraph/op/tan.hpp
        # include/ngraph/op/quantized_convolution.hpp
        # include/ngraph/op/negative.hpp
        # include/ngraph/op/relu.hpp
        # include/ngraph/op/any.hpp
        # include/ngraph/op/assign.hpp
        # include/ngraph/op/depth_to_space.hpp
        # include/ngraph/op/reduce_logical_or.hpp
        # include/ngraph/op/floor_mod.hpp
        # include/ngraph/op/stop_gradient.hpp
        # include/ngraph/op/slice.hpp
        # include/ngraph/op/embeddingbag_offsets_sum.hpp
        # include/ngraph/op/shape_of.hpp
        # include/ngraph/op/lrn.hpp
        # include/ngraph/op/transpose.hpp
        # include/ngraph/op/embeddingbag_packedsum.hpp
        # include/ngraph/op/mod.hpp
        # include/ngraph/op/max.hpp
        # include/ngraph/op/proposal.hpp
        # include/ngraph/op/roi_pooling.hpp
        # include/ngraph/op/read_value.hpp
        # include/ngraph/op/floor.hpp
        # include/ngraph/op/prelu.hpp
        # include/ngraph/op/strided_slice.hpp
        # include/ngraph/op/quantized_dot.hpp
        # include/ngraph/op/lstm_sequence.hpp
        # include/ngraph/op/rnn_cell.hpp
        # include/ngraph/op/region_yolo.hpp
        # include/ngraph/op/reverse.hpp
        # include/ngraph/op/acos.hpp
        # include/ngraph/op/less.hpp
        # include/ngraph/op/detection_output.hpp
        # include/ngraph/op/reduce_sum.hpp
        # include/ngraph/op/psroi_pooling.hpp
        # include/ngraph/op/embedding_segments_sum.hpp
        # include/ngraph/op/asin.hpp
        # include/ngraph/op/concat.hpp
        # include/ngraph/op/gather_nd.hpp
        # include/ngraph/op/prior_box.hpp
        # include/ngraph/op/squeeze.hpp
        # include/ngraph/op/gather_tree.hpp
        # include/ngraph/op/not_equal.hpp
        # include/ngraph/op/erf.hpp
        # include/ngraph/op/minimum.hpp
        # include/ngraph/op/replace_slice.hpp
        include/ngraph/op/op.hpp
        # include/ngraph/op/or.hpp
        # include/ngraph/op/acosh.hpp
        # include/ngraph/op/dequantize.hpp
        # include/ngraph/op/reorg_yolo.hpp
        # include/ngraph/op/range.hpp
        # include/ngraph/op/log.hpp
        # include/ngraph/op/sqrt.hpp
        # include/ngraph/op/select.hpp
        # include/ngraph/op/sum.hpp
        # include/ngraph/op/scatter_update.hpp
        # include/ngraph/op/max_pool.hpp
        # include/ngraph/op/prior_box_clustered.hpp
        # include/ngraph/op/sigmoid.hpp
        # include/ngraph/op/reshape.hpp
        # include/ngraph/op/cum_sum.hpp
        # include/ngraph/op/shuffle_channels.hpp
        # include/ngraph/op/subtract.hpp
        # include/ngraph/op/ctc_loss.hpp
        # include/ngraph/op/softplus.hpp
        # include/ngraph/op/avg_pool.hpp
        # include/ngraph/op/reduce_l2.hpp
        # include/ngraph/op/gather.hpp
        include/ngraph/op/parameter.hpp
        # include/ngraph/op/tanh.hpp
        # include/ngraph/op/broadcast.hpp
        # include/ngraph/op/group_conv.hpp
        # include/ngraph/op/sinh.hpp
        # include/ngraph/op/lstm_cell.hpp
        # include/ngraph/op/not.hpp
        # include/ngraph/op/scatter_nd_update.hpp
        # include/ngraph/op/split.hpp
        # include/ngraph/op/matmul.hpp
        # include/ngraph/op/reduce_l1.hpp
        # include/ngraph/op/convert.hpp
        include/ngraph/visibility.hpp
        include/ngraph/runtime/tensor.hpp
        include/ngraph/runtime/host_tensor.hpp
        include/ngraph/runtime/aligned_buffer.hpp
        include/ngraph/shape.hpp
        include/ngraph/variant.hpp
        include/ngraph/dimension.hpp
        include/ngraph/node_output.hpp
        include/ngraph/ngraph_visibility.hpp
        include/ngraph/except.hpp
        include/ngraph/type/element_type_traits.hpp
        include/ngraph/type/element_type.hpp
        include/ngraph/type/bfloat16.hpp
        include/ngraph/type/float16.hpp
        include/ngraph/node.hpp
        include/ngraph/strides.hpp
        include/ngraph/output_vector.hpp
        include/ngraph/attribute_visitor.hpp
        include/ngraph/slice_plan.hpp
        include/ngraph/coordinate.hpp
        include/ngraph/descriptor/tensor.hpp
        include/ngraph/descriptor/output.hpp
        include/ngraph/descriptor/input.hpp
        include/ngraph/rank.hpp
        include/ngraph/evaluator.hpp
        include/ngraph/axis_vector.hpp
        # include/ngraph/validation_util.hpp
        include/ngraph/chrome_trace.hpp
        include/ngraph/ops.hpp
        include/ngraph/pattern/op
        include/ngraph/pattern/op/true.hpp
        include/ngraph/pattern/op/any_of.hpp
        include/ngraph/pattern/op/label.hpp
        include/ngraph/pattern/op/skip.hpp
        include/ngraph/pattern/op/pattern.hpp
        include/ngraph/pattern/op/branch.hpp
        include/ngraph/pattern/op/any.hpp
        include/ngraph/pattern/op/or.hpp
        include/ngraph/pattern/op/capture.hpp
        include/ngraph/pattern/op/any_output.hpp
        include/ngraph/pattern/op/wrap_type.hpp
        include/ngraph/pattern/matcher.hpp
        include/ngraph/util.hpp
        include/ngraph/log.hpp
        include/ngraph/distributed.hpp
        include/ngraph/provenance.hpp
        include/ngraph/ngraph.hpp
        include/ngraph/axis_set.hpp
        include/ngraph/node_input.hpp
        include/ngraph/deprecated.hpp
        include/ngraph/factory_adapter.hpp
        include/ngraph/coordinate_diff.hpp
        include/ngraph/file_util.hpp
    )
# Create shared library
add_library(ngraph SHARED ${SRC})

set_target_properties(ngraph PROPERTIES
                      CXX_VISIBILITY_PRESET hidden
                      C_VISIBILITY_PRESET hidden
                      VISIBILITY_INLINES_HIDDEN ON)

target_link_libraries(ngraph PRIVATE openvino::itt ngraph::builder ngraph::reference)

find_package(Graphviz QUIET)
if (GRAPHVIZ_FOUND)
    set_property(SOURCE pass/visualize_tree.cpp APPEND PROPERTY COMPILE_DEFINITIONS GRAPHVIZ_FOUND)
endif()

if(NGRAPH_ADDRESS_SANITIZER)
    message(STATUS "Enable Address Sanitizer")
    add_compile_options(-g -fsanitize=address -fno-omit-frame-pointer)
endif()

if(NGRAPH_LIB_VERSIONING_ENABLE)
    set_target_properties(ngraph PROPERTIES
        VERSION ${NGRAPH_VERSION}
        SOVERSION ${NGRAPH_API_VERSION})
endif()
target_compile_definitions(ngraph PUBLIC NGRAPH_VERSION="${NGRAPH_VERSION}")

if (LINUX)
    # nGraph links against one or more libraries (ex. LLVM) but we don't want to
    # export these symbols as part of the DSO. This is a GNU ld (and derivatives) specific
    # option so making this portable is still an open issue. As a note for the future,
    # this is not an issue on Windows and LLVM's lld does support --exclude-libs.
    set_property(TARGET ngraph APPEND_STRING PROPERTY LINK_FLAGS " -Wl,--exclude-libs,ALL")

    # GCC invokes the linker with --as-needed by default which doesn't work for us
    # because generated code needs to find symbols in these DSOs at runtime.
    # The fix below is temporary and will be removed once we find a better way
    # to do this because certain dependencies like the OpenMP runtime libraries
    # _do_ need to be linked with --as-needed with a higher priority for the
    # Intel OpenMP runtime so we don't mix libgomp and libiomp5
    if (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
        set_property(TARGET ngraph APPEND_STRING PROPERTY LINK_FLAGS " -Wl,--no-as-needed")
    endif()
elseif(APPLE)
    set_property(TARGET ngraph APPEND_STRING PROPERTY LINK_FLAGS " -Wl,-rpath,@loader_path")
endif()

# Defines macro in C++ to load backend plugin
target_include_directories(ngraph PUBLIC $<BUILD_INTERFACE:${NGRAPH_INCLUDE_PATH}> $<INSTALL_INTERFACE:include>)
target_include_directories(ngraph PRIVATE ${NGRAPH_INCLUDE_DIR}
                                          ${NGRAPH_INCLUDE_DIR}/op
                                          ${NGRAPH_INCLUDE_DIR}/op/util
                                          ${NGRAPH_INCLUDE_DIR}/pass
                                          ${NGRAPH_INCLUDE_DIR}/pattern
                                          ${NGRAPH_INCLUDE_DIR}/pattern/op
                                          ${NGRAPH_INCLUDE_DIR}/runtime
                                          ${CMAKE_CURRENT_SOURCE_DIR}/src
                                          )

#Add an alias so that library can be used inside the build tree, e.g. when testing
add_library(ngraph::ngraph ALIAS ngraph)

if (NOT WIN32)
    target_link_libraries(ngraph PRIVATE dl)
endif()

# Build subdirectories for all build types on Windows
if(WIN32)
    foreach(BUILD_TYPE Release Debug RelWithDebInfo MinSizeRel)
        if(NOT EXISTS ${NGRAPH_BUILD_DIR}/${BUILD_TYPE})
            file(MAKE_DIRECTORY ${NGRAPH_BUILD_DIR}/${BUILD_TYPE})
        endif()
    endforeach()
endif()

#-----------------------------------------------------------------------------------------------
# Installation logic...
#-----------------------------------------------------------------------------------------------

# nGraph
install(TARGETS ngraph EXPORT ngraphTargets
        RUNTIME DESTINATION ${NGRAPH_INSTALL_LIB} COMPONENT ngraph
        ARCHIVE DESTINATION ${NGRAPH_INSTALL_LIB} COMPONENT ngraph
        LIBRARY DESTINATION ${NGRAPH_INSTALL_LIB} COMPONENT ngraph)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/
    DESTINATION ${NGRAPH_INSTALL_INCLUDE}/
    COMPONENT ngraph
    FILES_MATCHING
        PATTERN "*.hpp"
        PATTERN "*.h"
)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/include/ngraph/version.hpp
    DESTINATION ${NGRAPH_INSTALL_INCLUDE}/ngraph
    COMPONENT ngraph)

set(CPACK_GENERATOR "DEB")
set(CPACK_DEBIAN_PACKAGE_SHLIBDEPS ON)
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "nGraph library")
set(CPACK_PACKAGE_NAME "nGraph")
set(CPACK_PACKAGE_VENDOR "Intel")

set(CPACK_PACKAGE_VERSION_MAJOR ${NGRAPH_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR ${NGRAPH_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH ${NGRAPH_VERSION_PATCH})
include(CPack)
