<script setup>
  import { computed, ref } from 'vue';
  import Container from "@/components/Container.vue";
  import Row from "@/components/Row.vue"
  import CountryCard from "@/components/main/Countrycard.vue"
  import CountryFilter from '@/components/main/CountryFilter.vue'
  

  const countries = [
  {
    "flags": {
      "png": "https://flagcdn.com/w320/de.png",
      "svg": "https://flagcdn.com/de.svg",
      "alt": "The flag of Germany is composed of three equal horizontal bands of black, red and gold."
    },
    "cca2": "DE",
    "name": {
      "common": "Germany",
      "official": "Federal Republic of Germany"
    },
    "independent": true,
    "region": "Europe",
    "subregion": "Western Europe",
    "population": 83240525
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/py.png",
      "svg": "https://flagcdn.com/py.svg",
      "alt": "The flag of Paraguay features three equal horizontal bands of red, white and blue, with an emblem centered in the white band. On the obverse side of the flag depicted, this emblem is the national coat of arms."
    },
    "cca2": "PY",
    "name": {
      "common": "Paraguay",
      "official": "Republic of Paraguay"
    },
    "independent": true,
    "region": "Americas",
    "subregion": "South America",
    "population": 7132530
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/ag.png",
      "svg": "https://flagcdn.com/ag.svg",
      "alt": "The flag of Antigua and Barbuda has a red field with an inverted isosceles triangle based on the top edge and spanning the height of the field. This triangle has three horizontal bands of black, light blue and white, with the light blue band half the height of the two other bands. The top half of a golden-yellow sun is situated in the lower two-third of the black band to depict a rising sun."
    },
    "cca2": "AG",
    "name": {
      "common": "Antigua and Barbuda",
      "official": "Antigua and Barbuda"
    },
    "independent": true,
    "region": "Asia",
    "subregion": "Caribbean",
    "population": 97928
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/in.png",
      "svg": "https://flagcdn.com/in.svg",
      "alt": "The flag of India is composed of three equal horizontal bands of saffron, white and green. A navy blue wheel with twenty-four spokes — the Ashoka Chakra — is centered in the white band."
    },
    "cca2": "IN",
    "name": {
      "common": "India",
      "official": "Republic of India"
    },
    "independent": true,
    "region": "Asia",
    "subregion": "Southern Asia",
    "population": 1380004385
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/bf.png",
      "svg": "https://flagcdn.com/bf.svg",
      "alt": "The flag of Burkina Faso features two equal horizontal bands of red and green, with a yellow five-pointed star in the center."
    },
    "cca2": "BF",
    "name": {
      "common": "Burkina Faso",
      "official": "Burkina Faso"
    },
    "independent": true,
    "region": "Africa",
    "subregion": "Western Africa",
    "population": 20903278
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/hk.png",
      "svg": "https://flagcdn.com/hk.svg",
      "alt": ""
    },
    "cca2": "HK",
    "name": {
      "common": "Hong Kong",
      "official": "Hong Kong Special Administrative Region of the People's Republic of China"
    },
    "independent": false,
    "region": "Asia",
    "subregion": "Eastern Asia",
    "population": 7500700
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/ae.png",
      "svg": "https://flagcdn.com/ae.svg",
      "alt": "The flag of United Arab Emirates features a red vertical band on its hoist side that takes up about one-fourth the width of the field and three equal horizontal bands of green, white and black adjoining the vertical band."
    },
    "cca2": "AE",
    "name": {
      "common": "United Arab Emirates",
      "official": "United Arab Emirates"
    },
    "independent": true,
    "region": "Asia",
    "subregion": "Western Asia",
    "population": 9890400
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/km.png",
      "svg": "https://flagcdn.com/km.svg",
      "alt": "The flag of Comoros is composed of four equal horizontal bands of yellow, white, red and blue, with a green isosceles triangle superimposed on the hoist side of the field. This triangle has its base on the hoist end, spans about two-fifth the width of the field and bears a fly-side facing white crescent and four five-pointed white stars arranged in a vertical line along the opening of the crescent."
    },
    "cca2": "KM",
    "name": {
      "common": "Comoros",
      "official": "Union of the Comoros"
    },
    "independent": true,
    "region": "Africa",
    "subregion": "Eastern Africa",
    "population": 869595
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/pn.png",
      "svg": "https://flagcdn.com/pn.svg",
      "alt": ""
    },
    "cca2": "PN",
    "name": {
      "common": "Pitcairn Islands",
      "official": "Pitcairn Group of Islands"
    },
    "independent": false,
    "region": "Oceania",
    "subregion": "Polynesia",
    "population": 56
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/bg.png",
      "svg": "https://flagcdn.com/bg.svg",
      "alt": "The flag of Bulgaria is composed of three equal horizontal bands of white, green and red."
    },
    "cca2": "BG",
    "name": {
      "common": "Bulgaria",
      "official": "Republic of Bulgaria"
    },
    "independent": true,
    "region": "Europe",
    "subregion": "Southeast Europe",
    "population": 6927288
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/dj.png",
      "svg": "https://flagcdn.com/dj.svg",
      "alt": "The flag of Djibouti is composed of two equal horizontal bands of light blue and light green, with a white isosceles triangle superimposed on the hoist side of the field. The triangle has its base on the hoist end, spans about two-fifth the width of the field and bears a red five-pointed star at its center."
    },
    "cca2": "DJ",
    "name": {
      "common": "Djibouti",
      "official": "Republic of Djibouti"
    },
    "independent": true,
    "region": "Africa",
    "subregion": "Eastern Africa",
    "population": 988002
  },
  {
    "flags": {
      "png": "https://flagcdn.com/w320/la.png",
      "svg": "https://flagcdn.com/la.svg",
      "alt": "The flag of Laos is composed of three horizontal bands of red, blue and red. The blue band is twice the height of the red bands and bears a white circle at its center."
    },
    "name": {
      "common": "Laos",
      "official": "Lao People's Democratic Republic"
    },
    "cca2": "LA",
    "independent": true,
    "region": "Asia",
    "subregion": "South-Eastern Asia",
    "population": 7275556
  }
]
const applyRegion = region => regionFilter.value = region
const regionFilter = ref(undefined)
const visibleContries = computed(()=>{
  if(regionFilter.value){
    return countries.filter(country => country.region === regionFilter.value)
  }
  return countries
})
</script>


<template>
  <Container>
    <header>
        <div class="box-header">
          <h1 class="title">
            Atlas: The Ultimate Guide to the World
          </h1>
          <p class="subTitle">
            Atlas is a website that lists every country with their flags and facts. You can explore the world map, search by name or region, and filter by criteria. Learn about the world and its diversity with Atlas!
          </p>
        </div>
        <CountryFilter :region="regionFilter" @select-region="applyRegion"/>
    </header>
    <Row tag="ul" :is-wrap="true">
      <CountryCard v-for="item in visibleContries" :country="item" :key="item.cca2"/>
    </Row>
  </Container>
</template>


<style scoped>
header{
  display: flex;
  flex-flow: row nowrap;
}
  .box-header{
    display: flex;
    flex-direction: column;
  }
</style>