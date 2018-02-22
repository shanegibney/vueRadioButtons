<style scoped>

h1,
h2 {
    font-weight: normal;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    /* display: inline-block; */
    margin: 0 10px;
}

a {
    color: #42b983;
}

</style>

<template>

<div>
    <div class="users">
        <div class="row">
            <div class="col-md-12">
                <form v-on:submit="addInfo">
                    <br /> Add text:
                    <input type="text" v-model="newInfo.text" placeholder="text">
                    <br />
                    <br />
                    <label for="col1">column 1:</label>
                    <input type="radio" id="col1" value="one" v-model="newInfo.col">
                    <label for="col2">column 2: </label>
                    <input type="radio" id="col2" value="two" v-model="newInfo.col">
                    <br />
                    <br />
                    <input type="submit" value="Submit Text" class="btn btn-info">
                </form>
                <hr>
            </div>
        </div>
        <div class="row">
          <div class="col-md-3">
          </div>
            <div class="col-md-3">
                <ol>
                    <li v-for="item in info" v-if="item.col==='one'">
                        textt: {{ item.text }}
                    </li>
                </ol>
            </div>
            <div class="col-md-3">
                <ol>
                    <li v-for="item in info" v-if="item.col==='two'">
                        texta: {{ item.text }}
                    </li>
                </ol>
            </div>
            <div class="col-md-3">
            </div>
        </div>
    </div>
</div>

</template>

<script>

export default {
    name: 'hello',
    data() {
        return {
            newInfo: {
                text: '',
                col: 'one'
            },
            info: []
        }
    },
    methods: {
        addInfo: function(e) {
            // console.log('added');
            this.info.push({
                text: this.newInfo.text,
                col: this.newInfo.col
            });
            //clear newInfo
            this.newInfo = {
                text: '',
                col: 'one'
            };
            for (var i = 0; i < this.info.length; i++) {
                console.log("text: " + this.info[i].text + " col: " + this.info[i].col);
            }
            e.preventDefault();
        }
    }
}

</script>
