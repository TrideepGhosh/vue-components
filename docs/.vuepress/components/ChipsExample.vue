<template>
    <div>
        <div class="item-wrapper">
            <h5>Choice Chips</h5> 
            <Chip :text="place" :value="place" v-for="(place,index) in places" :key="index" @click.native="chipClicked(place)" :hide-remove="true" :class="['selection-chip',selectedPlaces.indexOf(place)>-1?'selected':'']"></Chip>
        </div>
        <div class="item-wrapper">
            <h5>Profile Chips</h5>
            <Chip :text="person.name" :value="person.name" @removed="removeChip" v-for="person in people" :key="person.name" class="profile-chip">
                <template v-slot:pre>
                    <Avatar :image-url="person.imageURL" :size="20"></Avatar>
                </template>
            </Chip>
        </div>
    </div>
</template>

<script>
export default {
    name:'ChipsExample',
    data() {
        return {
            places: ['London','Liverpool','Sounthampton','Leeds'],
            selectedPlaces:[],
            people: [{name:'John Doe', imageURL:'https://m.media-amazon.com/images/M/MV5BOThhZTkxMWMtY2UyYS00MTdlLTk1ZmMtZWQ0OWFkZjE2YTA1XkEyXkFqcGdeQXVyMjU0ODI4MzY@._V1_UX172_CR0,0,172,256_AL_.jpg'},{name:'Jane Doe', imageURL:'https://66.media.tumblr.com/3f6c3a89a576a4a09a2ea18c5f2d5da9/tumblr_pk0lqkbqM31ss2e34o1_1280.jpg'}]
        };
    },
    methods: {
        chipClicked(place) {
            let index=this.selectedPlaces.indexOf(place);
            if(index>-1)
                this.selectedPlaces.splice(index,1);
            else
                this.selectedPlaces.push(place);           
        },
        removeChip(value){
            this.people=this.people.filter(function(item) {
                return item.name!==value;
            });
        }
    },
    
};
</script>

<style lang="scss" scoped>
.chip {
	margin-right: 0.5rem;
	&.selection-chip {
		cursor: pointer;
		&.selected {
			background: #0B58D4;
		}
	}
	&.profile-chip {
		background-color: #0B58D4;
		.avatar {
			margin-right: 0.5rem;
		}
	}
}
</style>