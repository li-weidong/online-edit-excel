<template>
    <div class="home">
        <div class="header">在线编辑excel</div>
        <Table
            border
            :columns="columns"
            :data="data"
        ></Table>
    </div>
</template>

<script>
export default {
    name: 'home',
    props: {},
    data() {
        return {
            borderBlue: false,
            columns: [
                {
                    title: 'A',
                    key: 'A',
                    render: (h, params) => {

                        // console.log(params)
                        let { row } = params
                        if (row.showInput) {
                            return <Input type='textarea' value={row.A} style={"width:100%;height:100%;padding:0"} onOn-blur={() => {
                                row.showInput = false;
                                this.$set(this.data, params.index, row)
                            }}
                                onOn-change={(e) => {
                                    console.log(e)
                                    row.A = e.target.value
                                    // this.$set(this.data,params.index,row)
                                }}
                            />
                        }
                        return <div style={"width:100%;height:100%"}
                            ondblclick={() => {
                                
                            }}
                            onclick={() => {
                                this.data.forEach(item => {
                                    this.$set(item, 'showInput', false);
                                });
                                row.showInput = true;
                                this.$set(this.data, params.index, row);

                            }}
                            onblue={() => {
                                console.log('123')
                            }}
                        >{row.A}
                        </div>
                    }
                },
                {
                    title: 'B',
                    key: 'B',
                    render: () => {
                        // let params
                        // console.log(params)
                        return <div style="width:100%;height:100%"
                            ondblclick={() => {
                                console.log('双击s')
                            }}
                            onclick={() => {
                                console.log('单击')
                            }}>
                        </div>
                    }
                },
            ],
            data: [
                {
                    A: 'A1',
                    b: 18,
                    address: 'New York No. 1 Lake Park',
                    date: '2016-10-03',
                },
                {
                    a: 'Jim Green',
                    b: 24,
                    address: 'London No. 1 Lake Park',
                    date: '2016-10-01'
                },
                {
                    a: 'Joe Black',
                    b: 30,
                    c: 'Sydney No. 1 Lake Park',
                    d: '2016-10-02'
                },
                {
                    a: 'Jon Snow',
                    b: 26,
                    c: 'Ottawa No. 2 Lake Park',
                    d: '2016-10-04'
                }
            ]
        }
    },
    methods: {
        onCellClick(row, column, data, event) {
            console.log(row, column, data, event)
        },
        // doubleClick(handle, await = 1000, n = 2) {
        //     let count = 0;
        //     let timer = null;
        //     return function () {
        //         if (!timer) {
        //             timer = setTimeout(() => {
        //                 count = 0;
        //                 timer = null;
        //             }, await);
        //         }
        //         count++;
        //         if (count === n) {
        //             handle(arguments);
        //             count = 0;
        //             clearTimeout(timer);
        //             timer = null;
        //         }
        //     };
        // }
    }
}
</script>
<style lang="less" scoped>
.home {
    .header {
        height: 10vh;
        line-height: 10vh;
    }
    .ivu-table .border-blue {
        border: 1px solid green !important;
    }
    /deep/.ivu-table-cell {
        width: 100%;
        height: 100%;
        padding: 0px;
    }
}
.ivu-table /deep/.border-blue .ivu-table-cell {
    border: 1px solid green !important;
}
</style>
