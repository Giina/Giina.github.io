<template>
    <div>
        <m-header></m-header>
        <m-navbar></m-navbar>
        <div class="clearfix content-container list-container">
            <div class="row list">
                <div class="col-xs-9 list-filter">
                    <div class="filter-wrapper">
                        <ul class="filter-list has-child">
                            <li class="filter-list-head">领域</li>
                            <li class="filter-list-item" :class="{active:filterData['领域'].active===item}"
                                v-on:click="filterData['领域'].active=item"
                                v-for="item in filterData['领域'].data"><span>{{item}}</span></li>
                            <li class="child-filter-list-container">
                                <ul class="child-filter-list">
                                    <li class="child-filter-list-item"
                                        :class="{active:filterData['领域'].childData[filterData['领域'].active].active===item}"
                                        v-on:click="filterData['领域'].childData[filterData['领域'].active].active=item"
                                        v-for="item in filterData['领域'].childData[filterData['领域'].active].data"><span>{{item}}</span>
                                    </li>
                                </ul>
                            </li>
                        </ul>
                        <ul class="filter-list">
                            <li class="filter-list-head">成熟度</li>
                            <li class="filter-list-item" :class="{active:filterData['成熟度'].active===item}"
                                v-on:click="filterData['成熟度'].active=item"
                                v-for="item in filterData['成熟度'].data"><span>{{item}}</span></li>
                        </ul>
                        <ul class="filter-list">
                            <li class="filter-list-head">来源地</li>
                            <li class="filter-list-item" :class="{active:filterData['来源地'].active===item}"
                                v-on:click="filterData['来源地'].active=item"
                                v-for="item in filterData['来源地'].data"><span>{{item}}</span></li>
                            <span class="m-btn btn-filter-more">更多</span>
                        </ul>
                        <div class="filter-list-group" :class="{hide:isShrinkFilter}">
                            <ul class="filter-list has-child">
                                <li class="filter-list-head">领域</li>
                                <li class="filter-list-item" :class="{active:filterData['领域'].active===item}"
                                    v-on:click="filterData['领域'].active=item"
                                    v-for="item in filterData['领域'].data"><span>{{item}}</span></li>
                                <li class="child-filter-list-container">
                                    <ul class="child-filter-list">
                                        <li class="child-filter-list-item"
                                            :class="{active:filterData['领域'].childData[filterData['领域'].active].active===item}"
                                            v-on:click="filterData['领域'].childData[filterData['领域'].active].active=item"
                                            v-for="item in filterData['领域'].childData[filterData['领域'].active].data"><span>{{item}}</span>
                                        </li>
                                    </ul>
                                </li>
                            </ul>
                            <ul class="filter-list">
                                <li class="filter-list-head">成熟度</li>
                                <li class="filter-list-item" :class="{active:filterData['成熟度'].active===item}"
                                    v-on:click="filterData['成熟度'].active=item"
                                    v-for="item in filterData['成熟度'].data"><span>{{item}}</span></li>
                            </ul>
                            <ul class="filter-list">
                                <li class="filter-list-head">来源地</li>
                                <li class="filter-list-item" :class="{active:filterData['来源地'].active===item}"
                                    v-on:click="filterData['来源地'].active=item"
                                    v-for="item in filterData['来源地'].data"><span>{{item}}</span></li>
                            </ul>
                        </div>
                        <a href="javascript:void(0)" class="m-btn btn-more"
                           v-on:click="toggleMoreFilter">{{isShrinkFilter ? '更多筛选项目' : '收起筛选项目'}}</a>
                    </div>
                </div>
                <div class="col-xs-3 list-ad">
                    <div class="ad-wrapper">
                        <i class="m-icon"></i>
                        <router-link to="/" class="ad-link">向迈科技寻求更多技术>></router-link>
                    </div>
                </div>
                <div class="col-xs-12 list-wrapper">
                    <ul class="sort-list">
                        <li class="sort-list-item" v-on:click="sortChanged('默认')" :class="{active:sortKey.value==='默认'}"><b>默认</b>
                        </li>
                        <li class="sort-list-item" v-on:click="sortChanged('人气')" :class="{active:sortKey.value==='人气'}"><b>人气<i
                                class="im-icon"></i></b></li>
                        <li class="sort-list-item" v-on:click="sortChanged('发布时间')" :class="{active:sortKey.value==='发布时间'}"><b>发布时间<i
                                class="im-icon"></i></b></li>
                    </ul>

                    <div class="list-null-hint">
                        “转基因”搜索结果较少，迈科技推荐您使用
                        <router-link to="/">技术资源推荐服务</router-link>
                    </div>
                    <div class="row">
                        <router-link
                                v-for="technology in technologyList" :to="{path:'technology',query:{id:technology.id}}"
                                class="col-lg-3 col-md-4 list-item">
                            <div class="list-item-img" v-bind:style="{'background-image':technology.cover}"></div>
                            <div class="clearfix list-item-caption">
                                <div class="row">
                                    <h5 class="col-xs-12 list-item-title" v-if="technology.title">{{technology.title}}</h5>
                                    <span class="col-lg-4 col-xs-6" v-if="technology.areas" v-for="area in technology.areas"><i
                                            class="m-icon"></i>{{technology}}</span>
                                    <span class="col-lg-4 col-xs-6" v-if="technology.countryFrom"><i
                                            class="m-icon"></i>{{technology.countryFrom}}</span>
                                    <span class="col-lg-4 col-xs-6" v-if="technology.maturity"><i class="m-icon"></i>{{technology.maturity}}</span>
                                    <span class="col-lg-4 col-xs-6 special"><i class="m-icon"></i>联系技术方</span>
                                </div>
                            </div>
                        </router-link>
                    </div>

                    <m-pagination class="list-pagination" :total="page.total" :current="page.current"
                                  size="page.size"></m-pagination>
                </div>
                <div class="col-xs-12 recommend-wrapper">
                    <span class="recommend-title">相关服务推荐</span>
                    <div class="col-xs-12 recommend-content">
                    </div>
                    <!--<li class="col-xs-4 recommend-content-item">-->
                    <!--<router-link to="/">-->
                    <!--<span class="number">01</span>-->
                    <!--<h3>推荐技术资源</h3>-->
                    <!--<h5>明确的技术难题</h5>-->
                    <!--<p>·针对具体需求，精准推荐现有技术方案或可解决问题的技术方</p>-->
                    <!--<h5>模糊的技术方向</h5>-->
                    <!--<p>·围绕行业领域，定性推荐具有市场竞争力且优质可行的升级技术</p>-->
                    <!--</router-link>-->
                    <!--</li>-->
                    <!--<li class="col-xs-4 recommend-content-item">-->
                    <!--<router-link to="/">-->
                    <!--<span class="number">01</span>-->
                    <!--<h3>推荐技术资源</h3>-->
                    <!--<h5>明确的技术难题</h5>-->
                    <!--<p>·针对具体需求，精准推荐现有技术方案或可解决问题的技术方</p>-->
                    <!--<h5>模糊的技术方向</h5>-->
                    <!--<p>·围绕行业领域，定性推荐具有市场竞争力且优质可行的升级技术</p>-->
                    <!--</router-link>-->
                    <!--</li>-->
                    <!--<li class="col-xs-4 recommend-content-item">-->
                    <!--<router-link to="/">-->
                    <!--<span class="number">01</span>-->
                    <!--<h3>推荐技术资源</h3>-->
                    <!--<h5>明确的技术难题</h5>-->
                    <!--<p>·针对具体需求，精准推荐现有技术方案或可解决问题的技术方</p>-->
                    <!--<h5>模糊的技术方向</h5>-->
                    <!--<p>·围绕行业领域，定性推荐具有市场竞争力且优质可行的升级技术</p>-->
                    <!--</router-link>-->
                    <!--</li>-->
                </div>
            </div>
            <m-hanging-buttons></m-hanging-buttons>
        </div>
    </div>
</template>

<script>
    //  import 'muse-ui/less/base.less'
    //  import appBar from 'muse-ui/src/appBar'

    import api from '~plugins/api'
    import mHeader from '~components/mHeader.vue'
    import mNavbar from '~components/mNavbar.vue'
    import mFooter from '~components/mFooter.vue'
    import mPagination from '~components/mPagination.vue'
    import mHangingButtons from '~components/mHangingButtons.vue'

    export default{
        data: function () {
            return {
                page: {
                    current: 1,
                    size: 12,
                    total: 0
                },
                loading: false,
                filterData: {
                    '领域': {
                        active: '能源电力',
                        data: ['能源电力', '环境工程', '化学化工', '材料科技', '生农医药', '机械电子'],
                        childData: {
                            '能源电力': {
                                active: '电机',
                                data: ['供电/供电设备', '电机', '光伏', '风能利用', '电池', '其他']
                            },
                            '环境工程': {
                                active: '电机',
                                data: ['供电/供电设备1', '电机', '光伏', '风能利用', '电池', '其他']
                            },
                            '化学化工': {
                                active: '电机',
                                data: ['供电/供电设备2', '电机', '光伏', '风能利用', '电池', '其他']
                            },
                            '材料科技': {
                                active: '电机',
                                data: ['供电/供电设备3', '电机', '光伏', '风能利用', '电池', '其他']
                            },
                            '生农医药': {
                                active: '电机',
                                data: ['供电/供电设备4', '电机', '光伏', '风能利用', '电池', '其他']
                            },
                            '机械电子': {
                                active: '电机',
                                data: ['供电/供电设备5', '电机', '光伏', '风能利用', '电池', '其他']
                            }
                        }
                    },
                    '成熟度': {active: '生试', data: ['小试', '中试', '生试']},
                    '来源地': {active: '中国', data: ['中国', '国家1', '国家3', '国家2']}
                },
                isShrinkFilter: true,
                sortKey: {
                    value: '默认',
                    order: true
                },
                technologyList: []
            }
        },
        watch: {
            '$route': 'getTechnologyList'
        },
        created: function () {
            this.getTechnologyList()
        },
        methods: {
            getTechnologyList: function () {
                this.page.current = this.$route.query.page
                api.technologies.list({
                    _range_from: this.page.size * (this.$route.query.page - 1) + 1,
                    _range_size: this.page.size
                }).then(data => {
                    this.technologyList = data.data.technologies
                })
            },
            toggleMoreFilter: function (e) {
                this.isShrinkFilter = !this.isShrinkFilter
            },
            sortChanged: function (val) {
                if (val === '默认') {
                    this.sortKey.value = val
                } else if (val === this.sortKey.value) {
                    this.sortKey.order = !this.sortKey.order
                } else {
                    this.sortKey.value = val
                    this.sortKey.order = true
                }
            }
        },
        components: {
//      appBar,
            mHeader,
            mNavbar,
            mFooter,
            mHangingButtons,
            mPagination
        }
    }
</script>

<style lang="less">
    .list-container {

        .list {
            padding: 22px 0;

            .list-filter {
                /*display: inline-block;*/
                float: left;
                padding-right: .9%;
                width: 75%;

                .filter {
                    &-wrapper {
                        padding: 0 14px;
                        width: 100%;
                        border: 1px solid #1f86ed;
                        text-align: center;
                    }

                    &-list {
                        position: relative;
                        margin-bottom: 0;
                        padding: 10px 14px;
                        list-style: none;
                        color: #707070;
                        font-size: 14px;
                        border-bottom: 1px dotted #1f86ed;
                        text-align: left;

                        &-group {
                            height: 243px;
                            overflow: hidden;
                            transition: height .2s ease-in-out;

                            &.hide {
                                height: 0;
                            }
                        }

                        &-head {
                            display: inline-block;
                            margin-right: 21px;
                            font-weight: bold;
                        }

                        &-item {
                            display: inline-block;
                            cursor: pointer;

                            span {
                                display: block;
                                padding: 5px 18px;
                                border: 1px solid transparent;
                            }

                            &.active span {
                                border-color: #1f86ed;
                                border-radius: 4px;
                                background-color: #f4f8fd;
                                font-weight: bold;
                                color: #0A539A;
                            }
                        }

                        &.has-child {
                            padding-top: 0;
                            padding-bottom: 0;

                            .filter-list-item {
                                padding: 10px 12px;

                                &.active {
                                    background-color: #f4f8fd;
                                }
                            }
                        }

                        .btn-filter-more {
                            position: absolute;
                            right: 14px;
                            top: 10px;
                            padding: 5px 18px;
                            border: 1px solid #1f86ed;
                            border-radius: 4px;
                            background-color: #f4f8fd;
                            font-weight: bold;
                            color: #0A539A;
                            cursor: pointer;
                        }
                    }
                }

                .child-filter-list {
                    margin-left: -28px;
                    margin-right: -28px;
                    padding: 10px 28px;
                    list-style: none;
                    color: #707070;
                    font-size: 14px;
                    text-align: left;
                    background-color: #f4f8fd;

                    &-item {
                        display: inline-block;
                        padding: 5px 0;
                        margin-right: 12px;
                        cursor: pointer;
                        border: 1px solid transparent;

                        span {
                            padding: 0 16px;
                        }

                        &:first-child {
                            margin-left: -17px;
                        }

                        &.active {
                            border-color: #1f86ed;
                            border-radius: 4px;
                            background-color: #f4f8fd;
                            font-weight: bold;
                            color: #0A539A;
                        }
                    }
                }

                .btn-more {
                    display: inline-block;
                    margin-top: 15px;
                    margin-bottom: 15px;
                    width: 120px;
                    height: 30px;
                    line-height: 28px;
                    border: 1px solid #1f86ed;
                    border-radius: 4px;
                    background-color: #f4f8fd;
                    text-decoration: none;
                    color: #0A539A;
                    font-size: 14px;
                }
            }

            .list-ad {
                display: inline-block;
                width: 25%;

                .ad-wrapper {
                    padding: 72px 0;
                    height: 273px;
                    background-color: #f4f8fd;
                    text-align: center;

                    .m-icon {
                        margin: 0 auto;
                        height: 66px;
                        width: 66px;
                        background-color: black;
                    }
                }

                .ad-link {
                    margin-top: 34px;
                    font-size: 18px;
                    color: #1f86ed;
                }
            }

            .sort {
                &-list {
                    margin-top: 30px;
                    width: 100%;
                    height: 40px;
                    border-bottom: 1px solid #D7D6D6;

                    &-item {
                        float: left;
                        margin-right: -1px;
                        width: 100px;
                        height: 40px;
                        line-height: 40px;
                        border: 1px solid #D7D6D6;
                        border-bottom: none;
                        text-align: center;
                        cursor: pointer;

                        &.active {
                            border-top: 4px solid #1f86ed;
                            color: #1f86ed;
                        }
                    }
                }
            }

            &-wrapper {
                width: 100%;

                .list-item {
                    margin-top: 18px;

                    &:hover {
                        color: #1f86ed;
                    }

                    &-img {
                        height: 171px;
                        background-color: #1f86ed;
                    }

                    &-title {
                        padding-left: 5px;
                        padding-right: 5px;
                        line-height: 1.4;
                        font-size: 16px;
                        color: #707070;
                        font-weight: bold;

                        &:hover {
                            color: #1f86ed;
                        }
                    }

                    &-caption {
                        font-size: 12px;
                        line-height: 20px;
                        padding: 0 2px 2px 6px;
                        border: 1px solid #eee;

                        .m-icon {
                            display: inline-block;
                            margin-right: 4px;
                            height: 14px;
                            width: 14px;
                            background-color: black;
                            vertical-align: text-bottom;
                        }

                        .row {
                            margin-left: -5px;
                            margin-right: -5px;
                        }

                        span {
                            padding-left: 5px;
                            padding-right: 5px;

                            &.special {
                                color: #F7B52D;
                                font-weight: bold;
                            }
                        }

                        a {
                            color: #F7B52D;
                        }
                    }
                }
            }

            .recommend {
                &-wrapper {
                    margin-bottom: 30px;
                }

                &-title {
                    display: block;
                    margin-top: 22px;
                    margin-bottom: 18px;
                    width: 120px;
                    height: 20px;
                    line-height: 22px;
                    font-size: 18px;
                    padding-right: 6px;
                    border-right: 5px solid #F7B52D;
                    color: #1F86ED;
                    font-weight: bold;
                }

                &-content {
                    height: 240px;
                    background-color: gray;

                    &-item {
                        span {
                        }

                        h3 {
                        }

                        h5 {
                        }

                        p {
                        }
                    }
                }
            }

            &-null-hint {
                padding: 28px 36px;
                font-size: 18px;
                border: 1px solid #1f86ed;
                background: #f4f8fd;
                color: #707070;
                font-weight: bold;

                a {
                    display: inline-block;
                    color: #1f86ed;
                }
            }
        }

        .hb {
            right: 10%;
            margin-right: -100px;
        }

        .list-wrapper {
            width: 100%;
        }

        .list-pagination {
            text-align: right;

            .pagination {
                .active {
                    a {
                        background-color: #1f86ed;
                        color: #fff;
                    }
                }

                a {
                    margin-left: 5px;
                    margin-right: 5px;
                    border-color: #eee;
                    color: #1f86ed;
                }
            }
        }
    }
</style>

