<template>
        <div class="wrapper">
            <h5>Card with Collapsable Area</h5>
            <Card
                title="John Doe"
                :options="cardOptions"
                sub-title="developer at e9ine"
                card-media-image="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80"
                card-supporting-text="Lorem ipsum dolor sit, amet consectetur adipisicing elit. ">
                <template v-slot:cardExpandedContent>
                    <div class="expanded-content-example">
                        <h6>Example Expanded Content</h6>
                        <p class="body-s">
                            Expanded content is not visible by default. User needs to press on the expand title. Users can also pass a custom title name.
                        </p>
                        <div class="highlights">
                            <img src="https://randomuser.me/api/portraits/women/44.jpg" alt="">
                            <img src="https://randomuser.me/api/portraits/men/18.jpg" alt="">
                            <img src="https://randomuser.me/api/portraits/men/32.jpg" alt="">
                            <img src="https://randomuser.me/api/portraits/women/9.jpg" alt="">
                        </div>
                    </div>
                </template>
            </Card>
        </div>
</template>

<script>
    export default {
        name: 'CardExpandedSlotExample',
        data () {
            return {
                cardOptions: {
                    avatarOptions: {
                        text:'John Doe',
                        imageUrl:'https://images.unsplash.com/photo-1514543250559-83867827ecce?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2211&q=80'
                    },
                    expandedContentTitle: 'Expand Connections',
                    actions: [{
                        name: 'Click and Nav',
                        href: 'https://www.google.com',
                        clickAction: this.sayHi
                    }, {
                        name: 'Hello',
                        clickAction: this.sayHello
                    }, {
                        name: 'Navigate',
                        href: 'https://www.yahoo.com',
                    }],
                    cardInfoLocation: 'middle'
                }
            };
        },
        methods: {
            sayHi() {
                alert('Hi');
            },
            sayHello() {
                alert('Hello');
            }
        }
    };
</script>

<style lang="scss" scoped>
    .wrapper {
        margin-bottom: 32px;
        .card{
            width:320px;
        }
    }
    .expanded-content-example {
        padding: 12px 16px 16px;
        background-color: #fff;
        h4 {
            margin: 0;
            color: #000;
            line-height: 28px;
        }
        p {
            font-size: 12px;
            color: #777;
        }
        .highlights {
            display: flex;
            justify-content: space-between;
            margin: 1.5rem 0 1rem;
            img {
                height: 56px;
                width: 56px;
                border-radius: 32px;
                margin-right: 0;
            }
        }
    }
</style>
