<script lang="ts">
	import axios from "axios";

	export default class Request {
		public static instance: Request;

		public constructor() {}

		public static getInstance(): Request {
			if (!Request.instance) {
				Request.instance = new Request();
			}

			return Request.instance;
		}

		public async get(url: string): Promise<any> {
			return await this.request("get", url);
		}

		public async post(url: string, data: any): Promise<any> {
			return await this.request("post", url, data);
		}

		public async put(url: string, data: any): Promise<any> {
			return await this.request("put", url, data);
		}

		public async delete(url: string): Promise<any> {
			return await this.request("delete", url);
		}

		private async request(method: string, url: string, data?: any) {
			try {
				const response = await axios({
					method: method,
					url: url,
					data: data
				});

				return {
					isOk: true,
					data: response.data,
					status: response.status
				};
			} catch (error: any) {
				return {
					isOk: false,
					data: error.response.data,
					status: error.response.status
				};
			}
		}
	}
</script>
